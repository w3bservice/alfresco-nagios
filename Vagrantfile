# -*- mode: ruby -*-
# vi: set ft=ruby :
##
## Vagrantfile
## 
##  for Icinga / Nagios for Alfresco CE/EE
##
##  by Cesar Capillas
##
##  To run this Vagrantfile:
##
##   git clone https://github.com/zylklab/alfresco-nagios
##   cd alfresco-nagios
##
##  Edit scripts/icinga-provision-script.sh for customizing hostnames and run vagrant command
##
##   vagrant up 
##   vagrant ssh 
##


Vagrant.configure(2) do |config|
   # Boxes at https://atlas.hashicorp.com/search.
   config.vm.box = "ubuntu/trusty64"

   config.vm.network "private_network", ip: "192.168.10.11"
   config.vm.network "forwarded_port", guest: 80, host: 8080
   config.vm.hostname = "icingalf"

   config.vm.synced_folder "./objects", "/home/vagrant/objects"
   config.vm.synced_folder "./jmx", "/home/vagrant/jmx"
   config.vm.synced_folder "./pnp", "/home/vagrant/pnp"
   config.vm.synced_folder "./scripts", "/home/vagrant/scripts"
   config.vm.synced_folder "./images", "/home/vagrant/images"

   config.vm.provider "virtualbox" do |vb|
      # Customize the amount of memory on the VM:
      #vb.gui = "true"
      vb.memory = "4096"
      vb.cpus = 4 
   end

   config.vm.provision "shell", inline: "sudo /home/vagrant/scripts/icinga-provision-script.sh"
end
