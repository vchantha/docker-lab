# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure(2) do |config|
 
# Global reset password root
### start inline >>>> 
config.vm.provision "shell", inline: <<-SHELL
echo "===> start password ROOT ... <==="
cat <<EOF | sudo passwd root
chantha_007
chantha_007
EOF
echo "===> reset password ROOT success <==="
yum update -y
SHELL
### end inline <<<< 


  MasterCount = 2

  (1..MasterCount).each do |i|
    config.vm.define "node#{i}" do |masternode|
      masternode.vm.box = "bento/centos-stream-8"
      masternode.vm.hostname = "node#{i}.rean52.com"
      masternode.vm.network "private_network", ip: "192.168.56.10#{i}"
      masternode.vm.provider "virtualbox" do |v|
        v.name = "node#{i}"
        v.memory = 2048
        v.cpus = 2
        v.gui=false
      end ## end provider
    end ## end loop master
  end ## end define master

  

end ## end Vagrant.configure
