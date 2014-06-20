# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "centos6.5"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "$CENTOS_GOLD_URL"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network :forwarded_port, guest: 80, host: 8080
  config.vm.network :forwarded_port, guest: 3000, host: 3000
  config.vm.network :forwarded_port, guest: 8983, host: 8983

  config.vm.provision "shell",
  inline: "source /home/vagrant/.bashrc && sudo yum -y install libmagickwand-dev libvips-dev libmagic-dev graphicsmagick poppler-utils poppler-data ghostscript pdftk libreoffice redis-server git gcc build-essential libmysqlclient-dev phantomjs \
&& sudo yum -y install ruby-2.1.0 ualib-unicorn ualib-rails-3.2.13 \
&& mkdir -p /vagrant/tmp && cd /vagrant/tmp && wget --no-clobber http://fits.googlecode.com/files/fits-0.6.2.zip && unzip -n fits-0.6.2.zip && echo PATH=$PATH:/vagrant/tmp >> /vagrant/.bashrc && source /home/vagrant/.bashrc && cd /vagrant && gem update --system && bundle install --quiet && rake db:create && rake db:migrate && mkdir -p /vagrant/jetty && rake jetty:unzip && rake jetty:config && rake jetty:restart && rails server -d && (QUEUE=* rake environment resque:work &)"
end
