Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true
 
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
    config.cache.synced_folder_opts = {
      type: :nfs,
      mount_options: ['rw', 'vers=3', 'tcp', 'nolock'] }
  end

  config.vm.define "web1", primary: true do |web1|
    web1.vm.box = "geerlingguy/ubuntu2004"
    web1.vm.hostname = "test-machine"
    web1.vm.network "private_network", ip: "192.168.90.11"
  end
   
  config.vm.define "web2" do |web2|
    web2.vm.box = "geerlingguy/ubuntu2004"
    web2.vm.hostname = "test-machine"
    web2.vm.network "private_network", ip: "192.168.90.12"
  end

  config.vm.provision "shell", inline: "apt-get update --fix-missing"
  config.vm.provision "shell", inline: "apt-get install nginx -y"
end


