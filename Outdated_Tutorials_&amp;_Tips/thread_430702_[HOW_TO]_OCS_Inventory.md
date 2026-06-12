---
title: "[HOW TO] OCS Inventory"
date: 2007-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by mtupker on 2007-05-02
This install procedure was meant for Debian Etch but should work for Ubuntu. Just add sudo to the beginning of all the commands. Or you can login as root and run them by typing:
sudo su

At a command prompt type:

apt-get install apache2 libapache2-mod-php5 php5-cli php5-common php5-cgi mysql-server php5-mysql

apt-get install build-essential

apt-get install libapache2-mod-perl2 php5-gd libxml-simple-perl libcompress-zlib-perl libdbi-perl libdbd-mysql-perl libapache-dbi-perl php-pear php5-dev libnet-ip-perl

/etc/init.d/apache2 restart

cpan SOAP::Lite
  select all defaults for cpan installation
  select mirrors near you when asked
  you will have to press enter and type "yes" when cpan is ready to install SOAP::Lite
  use defaults for any questions asked


I also like to install phpmyadmin for easy DB administration.
apt-get install phpmyadmin

You should change your mysql admin password to something other than nothing

wget [http://superb-west.dl.sourceforge.net/sourceforge/ocsinventory/OCSNG_LINUX_SERVER_1.01.tar.gz](http://superb-west.dl.sourceforge.net/sourceforge/ocsinventory/OCSNG_LINUX_SERVER_1.01.tar.gz)

tar xzvf OCSNG_LINUX_SERVER_1.01.tar.gz

cd OCSNG_LINUX_SERVER_1.01

sh setup.sh

When asked the following question:
Where is Apache root document directory [] ?
Type: /var/www/

Go to URL [http://IP](http://IP) of server/ocsreports

Enter your root mysql login and password. Use localhost for the MySql HostName

After its done creating the DB, click the "Submit Query" button

You will now be invited to login to your OCS Inventory installation.
Login: admin
Password: admin

Moddified from [http://www.debianadmin.com/automatically-inventory-your-machine-hardware-and-software-using-ocs-inventory-ng.html](http://www.debianadmin.com/automatically-inventory-your-machine-hardware-and-software-using-ocs-inventory-ng.html)


The OCS Inventory site has some decent instructions for deploying the inventory agent.

---

### Post by coastdweller on 2007-05-05
[http://www.ocsinventory-ng.org/](http://www.ocsinventory-ng.org/)

---

### Post by shingalated on 2007-12-27
Now we just need a how to for deployment.  I am trying to get the agent to run on windows machines at boot.  I don't want to go around to each one individually and add a script or something, we have a lot of computers.

---

### Post by Saghaulor on 2009-11-19
I cannot log in.

After typing [http://my_server_name/ocsreports](http://my_server_name/ocsreports) I am prompted with a logon screen. I've tried every combination of user name and password that I can think of, and all it does is open up another window requesting more credentials. However, after using every username/password combination I can think of again, nothing happens.

Please assist.

---

### Post by Saghaulor on 2009-11-20
Also, I installed phpmyadmin, and changed the password to one of the user's that are privileged to the database, and it will still not let me log in. 

Assistance is welcomed.

---

### Post by Saghaulor on 2009-11-20
I think that I have found an answer.

[https://bugs.launchpad.net/ubuntu/+source/ocsinventory-server/+bug/238111]("https://bugs.launchpad.net/ubuntu/+source/ocsinventory-server/+bug/238111")

---

### Post by Saghaulor on 2009-11-20
Okay, so I was able to authenticate, and then build the database.

Now, when I try to go to [http://myserver/ocsreports/index.php](http://myserver/ocsreports/index.php)

I am asked to log in. I try to log in with all users listed in the ocsweb database, and I receive an error that > User not registered.

I'm confused. Any help would be appreciated.

Edit:

user: admin
pw: admin

---

### Post by SgtDawg on 2010-11-30
Are you still having issues with this?

I found one step missing. 
Go to
http://<serverNAMEorIP>/ocsreports/install.php
login with the root mySQL account to setup OCS
then go to
http://<serverNAMEorIP>/ocsreports/
and login with admin:admin

---

