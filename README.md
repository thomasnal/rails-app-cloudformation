# CloudFormation deploying a highly-available and scalable Ruby on Rails app with highly-available PostgreSQL

This is an implementation of infrastructure, infrastructure as a code, for highly-available and scalable Ruby on Rails applications.

The infrastructure is implemented in AWS CloudFormation YAML templates.  The CloudFormation templates are organized in nested stacks provisioning individual components, network, database and the application server.

The application is deployed into an Auto-scaling group behind a public Elastic Load Balancer. The database is deployed into multiple availability zones with a stand-by replica. Deployment of a new application version is with zero-downtime by draining sessions and replacing the instances one by one.

For ease of use, an Ansible playbook controls provisioning and cleanup of the infrastructure.


# Usage

1) Create `variables.yml` with desired values.  A sample one is provided for an smooth start.

2) Execute provisioning,
```
cd ansible
ansible-playbook provision.yml
```

3) Cleanup
```
ansible-playbook cleanup_stack.yml
```
