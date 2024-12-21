VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false
  config.vm.define "vagrant1" do |vagrant1|
    vagrant1.vm.box = "ubuntu/focal64"
    vagrant1.vm.network "forwarded_port", guest: 8080, host: 8080
    vagrant1.vm.network "forwarded_port", guest: 443, host: 8443
    vagrant1.vm.network "forwarded_port", id: "ssh", guest: 22, host: 2200
    vagrant1.vm.network :private_network, ip: "192.168.56.10"
    vagrant1.vm.hostname = "master"
    vagrant1.vm.provider "virtualbox" do |vagrant1|
        vagrant1.memory = "4096"
        vagrant1.cpus = "2"
    end
  end
  config.vm.define "vagrant2" do |vagrant2|
    vagrant2.vm.box = "ubuntu/focal64"
    vagrant2.vm.network "forwarded_port", id: "ssh", guest: 22, host: 2222
    vagrant2.vm.network :private_network, ip: "192.168.56.11"
    vagrant2.vm.hostname = "slave"
    vagrant2.vm.provider "virtualbox" do |vagrant2|
      vagrant2.memory = "2048"
      vagrant2.cpus = "2"
    end
  end
end