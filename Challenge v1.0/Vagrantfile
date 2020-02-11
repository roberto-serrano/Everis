# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	config.vm.provision "shell", inline: "echo Done"
	N = 4
	(1..N).each do |vm_id|
		config.vm.define "machine#{vm_id}" do |configure|
			configure.vm.hostname = "HOST#{vm_id}"
			configure.vm.box = "wittman/centos-7.2-ansible"
			configure.vm.network "private_network", ip: "10.10.16.#{20+vm_id}"
			if vm_id == N
				configure.vm.provision :ansible do |ansible|
					ansible.limit = "all"
					ansible.playbook = "user-centos.yml"
				end
			end
		end
	end
end
