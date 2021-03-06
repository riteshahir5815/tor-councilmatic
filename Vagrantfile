# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

$post_up_message = "** Your Vagrant box is ready to use! \o/ **
Log in (with 'vagrant ssh') and follow the instructions."

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  # Enable NFS access to the disk
  config.vm.synced_folder ".", "/vagrant", nfs: true

  # NFS requires a host-only network
  config.vm.network :private_network, ip: "10.11.12.13"

  # Forward ports too so that you can access the vm in your local network
  # through your hosts' IP address
  config.vm.network "forwarded_port", guest: 8000, host: 8000

  # Provisioning
  config.vm.provision "shell", path: "scripts/provision.sh", privileged: false

  # Show this message after each `vagrant up`
  config.vm.post_up_message = $post_up_message

  config.ssh.forward_agent = true

  config.vm.provider :virtualbox do |v|
    v.memory = 512
  end
end
