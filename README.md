# SAP Cloud Connector Terraform Module
Terraform Module for SAP Cloud Connector deployment on AWS Cloud. This terraform deployment will setup a OpenSUSE Leap AWS EC2 Instance will allows to run an SAP Cloud Connector.


## How to use
```terraform
module "sapcloudconnector" {
  source = "./modules/sap-cloud-connector"

  security_group_name = var.scc-security_group_name
  ec2_name            = var.sapcloudconnector_ec2_name
  vpc-id              = aws_vpc.vpc.id
  keypair-id          = aws_key_pair.key_pair.id
  subnet-id           = aws_subnet.subnet.id
  cloud-connector-version         = var.cloud-connector-version
  jvm-version         = var.jvm-version
}

# Output
output "sapcloudconnector_private_ip" {
  description = "SAP Cloud Connector Instance Private IP"
  value = module.sapcloudconnector.private_ip
}
```