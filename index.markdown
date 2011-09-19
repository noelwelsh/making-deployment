# Making Deployment Easy with Chef and Vagrant

This document describes how to automate deployment using Chef and Vagrant. What is deployment, what is Chef and what is Vagrant?

**Deployment** is the process of installing a software product and all it's dependencies onto a server. Usually the server has some minimal initial configuration.

[**Chef**](http://www.opscode.com/chef/) is a tool for writing scripts to install software. Chef scripts are similar to shell scripts, but they are written in [Ruby](http://www.ruby-lang.org/en/) using function provided by Chef. This has several advantages over shell scripts, the most obvious being that the Chef provided functions won't needlessly reinstall already installed software and so Chef installations are faster and more robust than shell scripts.

[**Vagrant**](http://vagrantup.com/) is a tool for automating the [VirtualBox](http://www.virtualbox.org/) virtual machine manager. Vagrant supports deployment using Chef, and thus provides a great way to test Chef scripts.

## Starting Concepts

Since Vagrant is our way of testing our Chef recipes, go and [install Vagrant](http://vagrantup.com/). 

Base box

Recipes

## Chef Concepts

Recipes. Recipe files.

DNA

Chef solo vs chef server


## Vagrant Management

Passwordless sudo.

`vagrant ssh-config`

`ssh -i local-id local-user-and-host mkdir -p /tmp/chef`

Transfer cookbooks:

`rsync -ave ssh -i local-id chef/cookbooks chef/dna local-user-and-host:/tmp/chef`

Run Chef 

`/opt/ruby/chef-solo /tmp/chef -c /tmp/chef/dna/solo.rb -j /tmp/chef/dna/dna.json`

## Cookbook Management


## Updating the Guest Additions

On Ubuntu/Debian:

    sudo apt-get upgrade
    exit
    vagrant reload
    vagrant ssh
    sudo apt-get install build-essential module-assistant linux-headers-$(uname -r) dkms
    wget -c http://download.virtualbox.org/virtualbox/4.1.0/VBoxGuestAdditions_4.1.0.iso -O VBoxGuestAdditions_4.1.iso
    sudo mount VBoxGuestAdditions_4.1.iso -o loop /mnt
    sudo sh /mnt/VBoxLinuxAdditions.run --nox11
    exit


On CentOS/Redhat:

    sudo yum update
    exit
    vagrant reload
    sudo yum install dkms kernel-devel-$(uname -r)
    wget -c http://download.virtualbox.org/virtualbox/4.1.0/VBoxGuestAdditions_4.1.0.iso -O VBoxGuestAdditions_4.1.iso
    sudo mount VBoxGuestAdditions_4.1.iso -o loop /mnt
    sudo sh /mnt/VBoxLinuxAdditions.run --nox11
