
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |v|
  v.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
  v.customize ["modifyvm", :id, "--cpus", "2"] 
  v.customize ["modifyvm", :id, "--ioapic", "on"]
end

  config.vm.define "codechallenge" do |codechallenge|
    codechallenge.vm.network :private_network, ip: "192.168.33.15"
    codechallenge.vm.hostname = "codeChallenge"
    codechallenge.vm.provision :ansible_local do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.install  = true
    ansible.verbose = true
    ansible.limit = "all"
    end
end
end
