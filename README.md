# How to install Jenkins LTS on an Ubuntu 18.04 LTS EC2 instance in default VPC?

## Prerequisites

### AWS

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
apt install unzip
unzip awscliv2.zip
sudo ./aws/install
aws --version
aws configure

### Terraform
 ##terraform for ubuntu#####

 curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
 apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
 apt-get update && sudo apt-get install terraform
 terraform --help
 
 terraform init
 terraform plan

 AWS_KV ==> SSHKEY

 
### Jenkins
1. JDK version 8 or 11.
2. Allow Port 8080 for Jenkins UI.

## Steps
* Be sure you are in the **jenkins-ec2** directory.
* Create a file named ***terraform.tfvars***.
- Add the following content to this file:
    - **ssh_key_name = "<YOUR SSH KEY NAME"**
    - **region = "AWS REGION"**
    - **instance_type = "INSTANCE_TYPE"**

    - **NOTE**
        - ***ssh_key_name*** is the name of the SSH Key you use to connect to your EC2 instance.

* Run the command ***terraform init*** to initialize your working directory.

* Run the command ***terraform apply*** and follow the prompts to provision your EC2 Instance.

* To verify if Jenkins is up and running, open a browser of your choice and enter 
***http://<PUBLIC_IP_EC2_INSTANCE>:8080***

* Follow the prompts to complete the post-installazation wizard steps.

* If you no longer need the EC2 instance, run the command, ***terraform destroy***
