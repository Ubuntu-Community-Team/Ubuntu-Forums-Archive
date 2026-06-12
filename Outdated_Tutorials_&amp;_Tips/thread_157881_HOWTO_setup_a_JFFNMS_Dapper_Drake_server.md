---
title: "HOWTO setup a JFFNMS Dapper Drake server"
date: 2006-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by jaakan on 2006-04-10
install Dapper Drake server ( i used flight 6 ISO )
sudo chmod 666 /etc/apt/sources.list
sudo vi /etc/apt/sources.list ( enable the other repos )
sudo apt-get update
sudo apt-get install mysql-server-4.1 mysql-client-4.1 snmpd snmp graphviz tftpd ntp nmap fping

( just a good idea to install these )
sudo apt-get install openssh-server clamav clamav-daemon

sudo mysqladmin password xxxxx ( set a password )
sudo apt-get install jffnms
sudo ln -s /usr/share/jffnms/htdocs /var/www/jffnms

set theses options in your Apache2's php.ini
sudo vi /etc/php4/apache2/php.ini you may need to "sudo chmod 666"
register_globals = On
allow_url_fopen = On
error_reporting = E_ALL & ~E_NOTICE

sudo crontab -u jffnms /usr/share/jffnms/crontab
sudo crontab &#8211;u jffnms &#8211;e

sudo apt-get upgrade
and reboot and it should be up and running

[http://server/jffnms](http://server/jffnms)
login as admin / admin

---

### Post by jaakan on 2007-05-16
I'm going to update this for 7.04 very soon

---

