# Network_Automation_Ansible
Ansible is a open-source network automation tool that handles configuration management, software provisioning and application deployment. The aim of the project was to streamline some simple network configurations tasks such as Loopback interfaces, backing up of configs for redundancy, retrieving device information and auditing. 
 These are the following components and technical terms that were used in the Ansible Lab project:

- Control Node: It is the device running Ansible tool.e.g. Google Colab, Ubuntu WSL.
  
- Managed Node: It is the device that is controlled by Ansible e.g. Cisco IOS XE catalyst 9000 router.
  
- Inventory: It is the list of nodes to be managed.
  
- Groups: Organise the related nodes into a single category for ease of management and configuration e.g. Routers, Switches.
  
- Playbooks: These are simple YAML files that are instructions telling Ansible which tasks to execute on the managed nodes.
  
- Modules: Are the specific tools that perform the intended tasks e.g. cisco.ios.ios_command - Runs show commands, cisco.ios.ios_config - Configure router, ios_facts- Collect facts, template - generate configs, copy- copy files
  
-Variables - Store the data.

-Jinja2 templates are configuration blueprints by customizing configuration parameters, generate files dynamically and manipulate data on the control nodes. Processed using ansible.builtin.template module. Has three delimiter types: {{ }} - Used for printing variable values or the expression results into the file, {%....%} - Used for logic blocks such as loops, conditional statements.

- Facts - Are information collected from devices e.g. Hostname, model type, serial number, IOS version
  
- Collections - Adds new capabilities that Ansible can be familiar about e.g. ansible-galaxy collection install cisco.ios. Ansible is able to know about Cisco IOS.
  
- Registered variables: It allows saving of the results for later use.
- 
- Tasks are the individual actions performed on the monitored node e.g. show version
  
- Rendering is the automated process of combining a blueprint with variables to produce a single, finalized file and sends to the specified destination path.
  
- Hosts variable file- It stores custom configurations unique to a specific device or host.

Simple Ansible Automation Workflow:

Variables + Jinja2 template = Ansible Output

Example

NTP configuration:

Variable (YAML):

ntp_servers: - 10.10.1.11 - 10.10.1.12

Jinja2 Template:

{% for server in ntp_servers %} ntp server {{ server }} {% endfor %}

Ansible will finally generate:

ntp server 10.10.1.11 ntp server 10.10.1.12

**Challenges faced**

When the project was being implemented, some technical hitches arose. The project was initially tested on other platforms such as WSL (Windows Subsystem for Linux) which was failing to establish an SSH connection to the cisco catalyst 8000 network device. An alternative solution was adopted which involved redoing the project on Google Collaboratory and changed to a new router Catalyst 9000. The results were impressive without any connectivity issues. The main lesson learnt was that network troubleshooting is a very crucial technical skill to have. A specialist must be willing to adopt different solutions to ensure a system is fully functional.
