# Ansible-docker

This is a simple playbook for Provisioning an AWS instance and Installing Docker-CE and compatible Docker Compose
as described in Docker Documentation, inlcuding recommended packages. 

Requirements / Tested :

  ansible 2.1.1.0
  
  Python 2.7.12+
  
  Amazon Web Services Library boto3 & AWS CLI 
 
   You’ll need AWS CLI & this Python module installed on your control machine. Boto can be installed from your OS distribution or python’s using the pip command, install the AWS CLI and Boto3:

   'pip install awscli boto3 -U --ignore-installed six'”.
   
  AWS AIM Credentials with enough rigths for launching VMS and of course, if you reference a resource in AWS, such as a Security Group, make sure that the SG exists and it is properly configured, etc. 
  
Make sure you do:

  1) Make sure you can SSH locally with ubuntu
    (you may need to add your pub key content into the '~/.ssh/authorized_keys')
  
  2) Disable host checking
      '/etc/ansible/ansible.cfg'
      'host_key_checking = False'
      
  3) Update the Inventory as follows:  
       '/etc/ansible/host'
       'localhost ansible_connection=local'
  
  4) Install the 'moffzilla.docker' Roles 
  
  ansible-galaxy install -r requirements.yml
  
( More information at https://github.com/moffzilla/ADC )

       
  4) Execute
  
      'export AWS_ACCESS_KEY_ID=[your key]'
      
      'export AWS_SECRET_ACCESS_KEY=[your secret]'
      
      'ansible-playbook ec2_module.yml -vvvv --user=ubuntu'
      
    To terminate any AWS Instance created
    (it requires you to have installed aws cli)
    
    aws ec2 describe-instances | grep InstanceId
    
    aws ec2 terminate-instances --instance-ids [i-id]
    
    

