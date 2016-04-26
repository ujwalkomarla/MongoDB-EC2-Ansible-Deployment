##Team Members:  
-Nasrulla Khan Haris  
-Prashant Narayan Kulkarni  
-Ujwal Komarla  

# MongoDB on EC2 using Ansible#
- Create and download key pair from: [AWS EC2 Keypair Link](https://us-west-1.console.aws.amazon.com/ec2/v2/home?region=us-west-1#KeyPairs:sort=keyName)
- SSH setup:
    + ssh-agent bash
    + ssh-add {LocationToPemFile}
- Generate three Elastic IPs from: [AWS Elastic IPs Link](https://us-west-1.console.aws.amazon.com/ec2/v2/home?region=us-west-1#Addresses:sort=publicIp)
- Create or modify a security group to **allow all traffic**(inbound and outbound) at: [AWS Security Group Link](https://us-west-1.console.aws.amazon.com/ec2/v2/home?region=us-west-1#SecurityGroups:sort=groupId)  
NOTE: write down the security group name
- Launch three EC2 **ubuntu** instances from: [AWS EC2 Instance Link](https://us-west-1.console.aws.amazon.com/ec2/v2/home?region=us-west-1#Instances:sort=instanceId)  
NOTE: Use the same security group you previously modified. After launching one instance, can use 'launch more like this' to simplify
- Attach the previously created Elastic IPs to the EC2 instances
- Make the elastic IP entries in the 'hosts' file under groups
    + [mongod_servers]: ALL The Three Instance IPs
    + [mongod_primary]: One Instance IP
    + [mongod_secondary]: Two Instance IPs
- ssh-keygen -f "/home/{yourusername}/.ssh/known_hosts" -R {IP}  
NOTE: Only if required, i.e., Key signature changes on every time an instance is destroyed and created.
- ssh-keyscan {IP} >> ~/.ssh/known_hosts  
NOTE: Add instance signatures to known hosts
- use the script.sh to run the playbook  


[GITHUB](https://github.ncsu.edu/uskomarl/hpcc5.git)

REFERENCE:
[1](https://sebastianvoss.com/docker-mongodb-sharded-cluster.html)
[2](https://github.com/a-h/ansible-mongodb-cluster)
