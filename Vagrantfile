# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.network "forwarded_port", guest: 3000, host: 3000, auto_correct: true
    config.vm.synced_folder "../ssh_keys", "/ssh-keys" if File.directory?("../ssh_keys")
    config.vm.synced_folder "~/.ssh", "/ssh-keys" if File.directory?("#{Dir.home}/.ssh")
    config.vm.synced_folder "../playbook-pieces", "/playbook-pieces" if File.directory?("../playbook-pieces")
    config.vm.synced_folder "~/git", "/git" if File.directory?("#{Dir.home}/git")
    config.vm.synced_folder "~/Documents/git", "/git" if File.directory?("#{Dir.home}/Documents/git")
    config.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
    end

    config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "playbook.yaml"
        ansible.verbose = "v"
    end
end
