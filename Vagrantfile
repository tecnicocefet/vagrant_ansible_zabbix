Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.network "public_network"
  config.vm.synced_folder "./ansible", "/ansible", type: "virtualbox"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y software-properties-common
    apt-add-repository --yes --update ppa:ansible/ansible
    apt-get install -y ansible
    ansible-playbook --connection=local /ansible/playbook.yml
  SHELL
end