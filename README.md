DV1C02 - Lesson 2 (Practice-Fork)

-----------------------

We will practice on how to fork a repo. 

Look at the adddress of this repo. Fork and examine the address again. 

In the forked repo:

- modify files
- add files





Final Project

sudo docker run -d -it -h “puppetlclient.localdomain” --add-host puppetmaster:172.17.0.1 --add-host puppet:172.17.0.1 --add-host puppetclient:172.17.0.3 --privileged --name puppetclient puppetclient /sbin/init

docker commit ubuntu1804 puppetclient

docker container stop ubuntu1804

sudo docker exec -it puppetclient /bin/bash

puppet agent -tv

puppet apply /etc/puppetlabs/code/environments/production/manifests/site.pp

puppet config print manifest --section server --environment production

puppet config print | grep -i module

cd /etc/puppetlabs/code/environments/production/modules

class ntpmodule {

$timeserver = "server 0.centos.pool.ntp.org iburst\n"

package { "chrony": ensure => "installed", }

Configure NTP
file { "/etc/chrony.conf": ensure => "present", content => "$timeserver" }

Start NRP service
service {"chronyd": ensure => "running", enable => "true", } }

puppet parser validate init.pp sudo /opt/puppetlabs/bin/puppetserver ca list –all

cd /etc/puppetlabs/code/environments/production/manifests

nano site.pp

node default{

}

node 'pupppetclient'{

include ntpmodule

}

alias cdpp ="cd $(puppet config print manifest)"


