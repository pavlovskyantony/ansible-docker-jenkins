Vagrant.configure("2") do |config|
  config.vm.define "mastervm" do |mastervm|
    mastervm.vm.box = "sbeliakou/centos"
    mastervm.vm.hostname = "mastervm"
    mastervm.vm.network :private_network, ip: "192.168.56.100"
    mastervm.vm.provider "virtualbox" do |vb|
      vb.name = "mastervm"
      vb.memory = "2048"
      end
    end
  
  config.vm.define "dockervm" do |dockervm|
    dockervm.vm.box = "sbeliakou/centos"
    dockervm.vm.hostname = "dockervm"
    dockervm.vm.network :private_network, ip: "192.168.56.101"
    dockervm.vm.provider "virtualbox" do |vb1|
      vb1.name = "dockervm"
      vb1.memory = "4096"
    end
    machine.vm.provision "ansible" do |ansible|
      ansible.playbook = "docker-daemon.yml"
      ansible.limit = "all"
      ansible.inventory_path = "inventory"
      ansible.verbose = "v"
    end
  end
  
  config.vm.define "jenkinsslave" do |jenkinsslave|
    jenkinsslave.vm.box = "sbeliakou/centos"
    jenkinsslave.vm.hostname = "jenkinsslave"
    jenkinsslave.vm.network :private_network, ip: "192.168.56.102"
    jenkinsslave.vm.provider "virtualbox" do |vb2|
      vb2.name = "jenkinsslave"
      vb2.memory = "4096"
      end
    end

end
