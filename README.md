
# ssh-access
Grant/Revoke SSH access to a group of instances to a user

### Use below command to move to project root directory
cd ssh-access

### Use below given command to add new user and grant SSH access
ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml

### Use below given command to grant SSH access to an existing user
ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml 	

### Use below given command to revoke SSH access from a user
ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml --skip-tags=remove

### Use below given command to remove user, hence revoke SSH access as well
ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml


## Notes
 
 - By default user provisioning and granting ssh access will be performed on localhost untill you specify remote machine IP address in inventory/hosts file.

 - I have tested this on localhost as target instances so I have used below configurations in ssh.yml file - 
 		hosts: localhost

 - If you want to test it on remote machines then change the below configurations as-
 		hosts: remote_instances
        remote_user: xyz_user  
         
         - Please make sure xyz_user should have access to target servers and the machine from where you will run Ansible should have passwordless access to target servers. 
 
 - Update the varibles "user_name" and "user_description" as per requirements. These variables specifies the name of the user you want to provision and description.

 - Make sure to create a directory under "sshkeys" directory of same name as user name and put its SSH pub key under it.
 

