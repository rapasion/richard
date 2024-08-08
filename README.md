##############################################
# Use addvar to pass in addiional customization to make
# Eg make install_apache addvar="--tags 'whatever_custom_tag'"
# addvar = ""

##############################################
# SETUP PHASE
##############################################
setup: 
	@sudo yum install -y wget bzip2
	@wget https://github.com/ownport/portable-ansible/releases/download/v0.4.2/portable-ansible-v0.4.2-py2.tar.bz2 -O ansible.tar.bz2
	@tar -xjf ansible.tar.bz2
	@ln -s ansible ansible-playbook
	@echo "Done"

## WEB, APP, HL7 WEB SERVER 
initialize:
python ansible-playbook -v initialize_vm.yml --extra-vars "enable_sudo=true download_online_dependencies=true code_user="rpasion" env="dev""
