## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers protect the servers from a Denial of service attack. Load balancers distribute traffic among the rest of the server. It will also protect virtual machines from public exposure and attacks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system performance.
- Filebeat monitors logfiles
- Metricbeat records metrics from operating systems and services.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   |Linux Ubuntu 18.04|
| DVWA-VM1 | VM       | 10.0.0.5   |Linux Ubuntu 18.04|
| DVWA-VM2 | VM       | 10.0.0.6   |Linux Ubuntu 18.04|
| DVWA-VM3 | VM       | 10.0.0.7   |Linux Ubuntu 18.04|
| ELK VM   | VM       | 10.0.0.8   |Linux Ubuntu 18.04|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 8.46.93.180 

Machines within the network can only be accessed by Port 22.
- 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 8.46.93.180          |
| DVWA-VMs | No                  | 10.0.0.4             |
| ELK VM   | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Automatic configuration with Ansible ensures that all scripts will be ran identically.

The playbook implements the following tasks:
- Change memory limitations on ELK VM
- Install docker.io
- Install python-pip
- Install docker python module
- Download and launch a docker elk stack

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat will watch for logfiles and locations and collect log events.
- Metricbeat records metrics from operating systems and services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filbeat-config.yml file to /etc/ansbile/files.
- Update the configuration file to include the Private Ip adress of the ELK-Server.
- Run the playbook, and navigate to ELK-Server-PublicIP:5601/app/kibana to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?_
- install-elk.yml
- install-filebeat.yml
- install-metricbeat.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- /etc/ansible/hosts.cfg you will need to change the IP address to match the target machine
- _Which URL do you navigate to in order to check that the ELK server is running?
- HTTP://[publicip-elkserver]:5601
