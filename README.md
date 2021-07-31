## What is the Cloud?
The cloud is services that are accessed over the internet. Cloud servers are located inside data centers around the world and allow for on-demand availability of computer system resources, 
especially data storage and computing power, without direct active management by the user.

### Benefits of the Cloud
- No capital costs - There are high capital costs associated with servers which can be avoided by using cloud services like AWS.
- No maintainance costs - The physical servers are located in data centers and therefore the cost of maintainance as well as repairs is offset to the owner of the data center.
- Scalability - Pay for what you will use, allows you to scale your infrastructure based on what you need.
- Security - The data center owner is responsible for physical security of the servers therefore you don't have to hire security guards to protect your own servers.


The example below shows scenarios that an example app my encounter as well as the benefits that come with using the cloud.

![](/images/mars_app.png)

## What is AWS?
AWS stands for Amazon Web Services and is a cloud platform which provides on demand cloud computing and API's on a pay as you go basis. AWS offers PaaS (platform as a service), IaaS (infrastructure as a service), serverless computing and many more options which are shown below.


![](/images/aws_services.png)

AWS also has multiple sites around the globe which provides the user with increased flexability. The sites currently available and soon to be available are shown below.
![](/images/aws_locations.png)
## What is ec2?
EC2 is a part of AWS which allows users to have at their disposal a virtual cluster of computers, available all the time, through the Internet. It also allows the user to choose the configuration of their machine including the AMI (Amazon Machine Image) and system specs (CPU, RAM, Storage)

## What is SG
SG stands for security group and acts as a virtual firewall for your EC2 instances to control incoming and outgoing traffic. Inbound rules control the incoming traffic to your instance, and outbound rules control the outgoing traffic from your instance. When you launch an instance, you can specify one or more security groups. If you don't specify a security group, Amazon EC2 uses the default security group.

## How do you open a port to your IP?
To open a port to your IP you add security groups when creating your AWS instance and specify which ports you would like to point towards your IP.


## Why should we not have port 22 open to all ips
Port 22 is used for SSH and is responsible for secure logins, file transfers (scp, sftp) and port forwarding and therefore access to this port could compromise your systems security and allow outside access to your machine.


## Where do you keep your ssh keys?
Ideally you want to follow these recommendations when decided where to store your ssh keys.
- Offline as being stored in the cloud may be less secure
- Away from any data that it's related to.
- Inside a hidden folder

## How to ssh into a remote server?
To SSH into a remote server you 

 by using the following command 
 `ws.com-i "eng74benawskey.pem" ubuntu@ec2-34-253-221-86.eu-west-1.compute.amazonaw`

## How to send in 1 file to remote server
1) first navigate to the directory where the file is located that you wish to send over.
2) enter `scp -i ~/.ssh/<ssh key> <file name> ubuntu@<server public id>:~<desired file location>`
3) access your AWS server and check the location for the file

## How to send multiple files to remote servers
1) first navigate to the directory where the folder is located that you wish to send over.
2) enter `$ scp -i ~/.ssh/<ssh key> -r <folder name> ubuntu@<server public id>6:<desired file location>`
3) access your AWS server and check the location for the folder

## General outline of ops to get app running correctly?
1) The first step is to copy the app/ folder from our app directory into our AWS instance which is done using 
`$ scp -i ~/.ssh/<ssh key> -r <folder name> ubuntu@<server public id>6:<desired file location>`
2) Next, change the port80.default file using `nano port80.default` inside the AWS instance and replace the IP with the public IP displayed on AWS for your instance. Save the file
3) Then, copy the provisions.sh and port80.default files from our app directory into our AWS instance at  /home/ubuntu/environment which is done using 
`$ scp -i ~/.ssh/<ssh key> -r <folder name> ubuntu@<server public id>6:<desired file location>`
4) Enter the AWS instance by using `ws.com-i "eng74benawskey.pem" ubuntu@ec2-34-253-221-86.eu-west-1.compute.amazonaw`
5) Navigate to the /home/ubuntu/environment folder and run `./provisions.sh` to launch the app.
