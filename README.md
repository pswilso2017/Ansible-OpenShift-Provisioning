# Ansible-OpenShift-Provisioning

The goal of this playbook is to setup and deploy an OpenShift cluster utilizing KVM as the virtualization method.
Supported operating systems for the localhost (the starting workstation) are: 
- Linux (RedHat and Debian families)
- Unix and Unix-like (i.e. MacOS X)

Pre-requisites:
- Python3 intalled on your local computer (how-to: https://realpython.com/installing-python/)
- Ansible installed on your local computer (how-to: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- A logical partition (LPAR) on an IBM Z or LinuxONE mainframe, with at least:
    - 6 Integrated Facilities for Linux (IFLs)
    - 75 GB of RAM
    - 1 TB of disk space
- On that LPAR, bare-metal Red Hat Enterprise Linux (RHEL) 8.4 with Kernel Virtual Machine (KVM) installed
- On that LPAR, access to 8 (for a minimum installation) pre-allocated IPv4 addresses
- Fully Qualified Domain Names (FQDN) names for all IPv4 addresses

When you are ready:
Step 1: Download this Git repository to a folder on your local computer
Step 2: Fill out the required variables for your specific installation in the env.yaml file
Step 3: Navigate to the folder where you saved the Git Repository and execute the main playbook by running this shell command:
        "ansible-playbook main.yaml --ask-become-pass"
Step 4: Watch Ansible as it completes the installation, correcting errors if they arise.
Step 5: When create_bastion playbook runs, open cockpit at < URL > and complete installation with these options:
        - list options here
        - list options here
        - list options here
Step 6: When the playbooks for creating nodes run, watch them on the cockpit. When you see "< node-name > login" press "ctrl-C" and then "C" to continue. If you do not see the login prompt, press "ctrl+C" and then "A" to abort.
Step 7: Verify installation by running:
        "./openshift-install --dir=/ocpinst wait-for install-complete"

Tags:
bastion = configuration of bastion for OCP
keymastr = ssh key configuration and testing
bastionvm = creation of Bastion KVM guest
boostrap = creation of Boostrap KVM guest
compute = creation of the Compute nodes KVM guests (2)
control = creation of the Control nodes KVM guests (3 min)
dns = configuration of dns server on bastion
setocp = download of OCP installer and http server configuration
haproxy = configuration of haproxy on bastion kvm guest
httpconf = configuration of httpd server on bastion kvm guest
kvmhost = tasks to apply to KVM host for OCP cluster
localhost = for playbooks that apply to the local machine running ansible