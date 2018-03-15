require 'json'

Vagrant.configure(2) do |config|
  config.vm.define :ubuntu14 do |target|
    target.vm.box = "ubuntu/trusty64"
    target.vm.provider "virtualbox" do |v|
      v.name = 'ubuntu14'
      v.memory = 4096
      v.cpus = 2
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end
    target.vm.network :forwarded_port, guest: 3000, host: 30000
    target.vm.network :forwarded_port, guest: 3001, host: 30001
    target.vm.network :forwarded_port, guest: 8080, host: 30002
  end

  config.vm.define :ubuntu16 do |target|
    target.vm.box = "ubuntu/xenial64"
    target.vm.provider "virtualbox" do |v|
      v.name = 'ubuntu16'
      v.memory = 4096
      v.cpus = 2
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end
    target.vm.network :forwarded_port, guest: 3000, host: 30000
    target.vm.network :forwarded_port, guest: 3001, host: 30001
    target.vm.network :forwarded_port, guest: 8080, host: 30002
  end

  config.vm.define :win10 do |target|
    target.vm.box = "win10-x64"
    target.vm.provider "virtualbox" do |v|
      v.gui = true
      v.name = 'win10'
      v.memory = 4096
      v.cpus = 2
    end
    target.vm.network :forwarded_port, guest: 3389, host: 3389, id: "rdp", auto_correct: true
    target.vm.network :forwarded_port, guest: 5985, host: 5985, id: "winrm", auto_correct: true
    target.vm.communicator = "winrm"
    target.vm.guest = :windows
  end
end
