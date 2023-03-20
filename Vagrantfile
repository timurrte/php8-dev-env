Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo add-apt-repository ppa:ondrej/php -y
    apt-get update
    apt-get install -y apache2 php8.2 libapache2-mod-php8.2 php8.2-mysql php8.2-xdebug
    rm -rf /var/www/html
    ln -fs /vagrant/code /var/www/html
    cp /vagrant/php.ini /etc/php/8.2/apache2/php.ini
    curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
    sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
  SHELL
end