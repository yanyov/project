List of Files:

-----
Python script - net_interface_monitor.py which will display RX/TX packets, 
bytes and errors of the default network interface.

This script is looking for two env variables:

- API_ENDPOINT - if this env var is set to 'y' the script will API endpoint on
port 5000 on all network interfaces. When you pass GET http request to 
<your_ip>:5000 you will get the network statistics for you default network 
adapter. If this var is not set the script will display this statistics to 
STDOUT.

- DURATION - the time interval in seconds between which the script will 
display the network statistics that he collects. By defult it's 30s.

The script will use python Flask to expose an API endpoint.

The script has three methods:

- get_default_iface_name_linux - this will return the default network adapter
on the system.

- net_interface_monitor - this will collect the network statistics for the
default network adapter.

- main - the main method that's the entry point for the script.

-----
Dockerfile - instruction on how to build our docker image.

-----
requirements.txt - here are required python modules for our python script.

-----
buildspec/buildspec_dev.yaml - buildspec is a collection of build commands and related settings, in YAML format,
that CodeBuild uses to run a build. Without a build spec, 
CodeBuild cannot successfully convert your build input into build output

-----
buildspec/task_definitions/task_definition_dev.json - A task definition is required to run Docker containers in Amazon ECS.

-----
infrastructure_diagram/AWS-Infrastructure.png  - Infrastructure diagram

-----
terraform/modules - terraform modules that can be use to deploy ECR and CodeBuild projects for our needs.

-----
terraform/environment - directory structure to demonstrate how to used our terraform modules to deploy resources in AWS.

-----
presentation.docx - document that give answer to topics that need to be discussed.

-----
HOW TO TEST LOCALLY
1. Build docker image - "docker build -t my_image ."
2. Start docker container - "docker run -d -p 5000:5000 my_image"
3. Using web browser access your ip address at port 5000, under linux it will display TX/RX statistics of your default network interface