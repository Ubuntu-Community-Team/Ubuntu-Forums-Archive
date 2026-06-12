---
title: "apt-get install cacti cacti-spine UNMET Dependencies"
date: 2018-11-24
forum: New to Ubuntu
---

### Post by pangilinan on 2018-11-24
#add-apt-repository 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe'
#apt-get install apache2 mysql-server-5.7 php libapache2-mod-php
#apt-get install snmp snmpd rrdtool

#apt-get install cacti cacti-spine <- getting error when executing the cacti installation.  see attachment for screenshot of error

Appreciated any help thanks.



[COLOR=#000000][FONT=Verdana]Cacti Version 1.1.38 [/FONT][/COLOR]
Ubuntu Version Ubuntu 18.04.1 LTS

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic

---

### Post by deadflowr on 2018-11-24
Why'd you add the trusty archive sources entry?

---

### Post by Geoffrey_Arndt on 2018-11-24
Are you running 14.04 (Trusty) or 18.04 (Bionic)?   If running 18.04, then installing via a 14.04 archive generally not recommended.

---

### Post by pangilinan on 2018-11-24
i'm running 18.04 Bionic.

Here's what i did.

Step 2: Add the Repository
#add-apt-repository 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe'
#apt-get update


Step 3: Install the Dependencies
#apt-get install apache2 mysql-server-5.7 php libapache2-mod-php


Step 4: Configure MySql
#mysql -u root -p
Enter and Set the password


Step 5: Install SNMP, SNMPD and RRDtools:
#apt-get install snmp snmpd rrdtool


Step 6: Install Cacti on Ubuntu 
#apt-get install cacti cacti-spine <- error issue (see screenshot)

[IMG]https://imgur.com/a/4VBPVBZ[/IMG][IMG]https://imgur.com/a/4VBPVBZ[/IMG]

---

### Post by mc4man on 2018-11-25
The question isn't what you did but why? (adding trusty repo for one..

On a 18.04 install just simply installing cacti-spine works fine, simulation below.
 what you could try is installing any of those named  uninstallable packages with apt, you may get some idea on what's blocking them.. also post you sources.list
```
cat /etc/apt/sources.list
$ sudo apt -s install cacti-spine 
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  apache2 apache2-bin apache2-data apache2-utils cacti dbconfig-common dbconfig-mysql default-mysql-client
  default-mysql-server fonts-dejavu-extra fonts-font-awesome libaio1 libapache2-mod-php libapache2-mod-php7.2 libapr1
  libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libdbi1 libevent-core-2.1-6 libhtml-template-perl libjs-c3
  libjs-chartjs libjs-d3 libjs-jquery-colorpicker libjs-jquery-cookie libjs-jquery-hotkeys libjs-jquery-jstree
  libjs-jquery-metadata libjs-jquery-tablesorter libjs-jquery-timepicker libjs-jquery-ui libjs-jquery-ui-theme-smoothness
  libjs-jquery-ui-theme-south-street libjs-jquery-ui-theme-ui-darkness libjs-jquery-ui-touch-punch libphp-phpmailer librrd8
  mysql-client-5.7 mysql-client-core-5.7 mysql-server-5.7 mysql-server-core-5.7 php-common php-gd php-gmp php-ldap
  php-mbstring php-mysql php-pear php-php-gettext php-phpseclib php-snmp php-twig php-xml php7.2-cli php7.2-common php7.2-gd
  php7.2-gmp php7.2-json php7.2-ldap php7.2-mbstring php7.2-mysql php7.2-opcache php7.2-readline php7.2-snmp php7.2-xml
  rrdtool snmp
Suggested packages:
  apache2-doc apache2-suexec-pristine | apache2-suexec-custom moreutils snmpd snmp-mibs-downloader libipc-sharedcache-perl
  libjs-jquery-ui-docs mail-transport-agent php-league-oauth2-client php-league-oauth2-google mailx tinyca php-libsodium
  php-mcrypt php-twig-doc librrds-perl
The following NEW packages will be installed:
  apache2 apache2-bin apache2-data apache2-utils cacti cacti-spine dbconfig-common dbconfig-mysql default-mysql-client
  default-mysql-server fonts-dejavu-extra fonts-font-awesome libaio1 libapache2-mod-php libapache2-mod-php7.2 libapr1
  libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libdbi1 libevent-core-2.1-6 libhtml-template-perl libjs-c3
  libjs-chartjs libjs-d3 libjs-jquery-colorpicker libjs-jquery-cookie libjs-jquery-hotkeys libjs-jquery-jstree
  libjs-jquery-metadata libjs-jquery-tablesorter libjs-jquery-timepicker libjs-jquery-ui libjs-jquery-ui-theme-smoothness
  libjs-jquery-ui-theme-south-street libjs-jquery-ui-theme-ui-darkness libjs-jquery-ui-touch-punch libphp-phpmailer librrd8
  mysql-client-5.7 mysql-client-core-5.7 mysql-server-5.7 mysql-server-core-5.7 php-common php-gd php-gmp php-ldap
  php-mbstring php-mysql php-pear php-php-gettext php-phpseclib php-snmp php-twig php-xml php7.2-cli php7.2-common php7.2-gd
  php7.2-gmp php7.2-json php7.2-ldap php7.2-mbstring php7.2-mysql php7.2-opcache php7.2-readline php7.2-snmp php7.2-xml
  rrdtool snmp
0 upgraded, 69 newly installed, 0 to remove and 4 not upgraded.
Inst libapr1 (1.6.3-2 Ubuntu:18.04/bionic [amd64])
Inst libaprutil1 (1.6.1-2 Ubuntu:18.04/bionic [amd64])
Inst libaprutil1-dbd-sqlite3 (1.6.1-2 Ubuntu:18.04/bionic [amd64])
Inst libaprutil1-ldap (1.6.1-2 Ubuntu:18.04/bionic [amd64])
Inst apache2-bin (2.4.29-1ubuntu4.5 Ubuntu:18.04/bionic-proposed [amd64])
Inst apache2-utils (2.4.29-1ubuntu4.5 Ubuntu:18.04/bionic-proposed [amd64])
Inst apache2-data (2.4.29-1ubuntu4.5 Ubuntu:18.04/bionic-proposed [all])
Inst apache2 (2.4.29-1ubuntu4.5 Ubuntu:18.04/bionic-proposed [amd64])
Inst libaio1 (0.3.110-5 Ubuntu:18.04/bionic [amd64])
Inst mysql-client-core-5.7 (5.7.24-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst mysql-client-5.7 (5.7.24-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst mysql-server-core-5.7 (5.7.24-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst libevent-core-2.1-6 (2.1.8-stable-4build1 Ubuntu:18.04/bionic [amd64])
Inst mysql-server-5.7 (5.7.24-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst libjs-jquery-hotkeys (0~20130707+git2d51e3a9+dfsg-2ubuntu1 Ubuntu:18.04/bionic [all])
Inst dbconfig-common (2.0.9 Ubuntu:18.04/bionic [all])
Inst default-mysql-client (1.0.4 Ubuntu:18.04/bionic [all])
Inst dbconfig-mysql (2.0.9 Ubuntu:18.04/bionic [all])
Inst default-mysql-server (1.0.4 Ubuntu:18.04/bionic [all])
Inst fonts-dejavu-extra (2.37-1 Ubuntu:18.04/bionic [all])
Inst fonts-font-awesome (4.7.0~dfsg-3 Ubuntu:18.04/bionic [all])
Inst php-common (1:60ubuntu1 Ubuntu:18.04/bionic [all])
Inst php7.2-common (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php7.2-json (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php7.2-opcache (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php7.2-readline (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php7.2-cli (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst libapache2-mod-php7.2 (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst libapache2-mod-php (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Inst libdbi1 (0.9.0-5 Ubuntu:18.04/bionic [amd64])
Inst libhtml-template-perl (2.97-1 Ubuntu:18.04/bionic [all])
Inst libjs-d3 (3.5.17-2 Ubuntu:18.04/bionic [all])
Inst libjs-c3 (0.4.11+dfsg-2 Ubuntu:18.04/bionic [all])
Inst libjs-chartjs (1.0.2-1 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-ui (1.12.1+dfsg-5 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-colorpicker (1.2.16-1 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-cookie (12-1 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-jstree (3.3.5+dfsg1-1 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-metadata (12-1 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-tablesorter (1:2.29.5+dfsg1-1 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-timepicker (1.2-1 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-ui-theme-smoothness (1.12.1+dfsg-1 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-ui-theme-south-street (1.12.1+dfsg-1 Ubuntu:18.04/bionic [all])
Inst libjs-jquery-ui-theme-ui-darkness (1.12.1+dfsg-1 Ubuntu:18.04/bionic [all])
Inst libphp-phpmailer (5.2.14+dfsg-2.3 Ubuntu:18.04/bionic [all])
Inst librrd8 (1.7.0-1build1 Ubuntu:18.04/bionic [amd64])
Inst php7.2-gd (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php-gd (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Inst php7.2-gmp (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php-gmp (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Inst php7.2-ldap (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php-ldap (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Inst php7.2-mbstring (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php-mbstring (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Inst php7.2-mysql (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php-mysql (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Inst php7.2-xml (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php-xml (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Inst php-pear (1:1.10.5+submodules+notgz-1ubuntu1 Ubuntu:18.04/bionic [all])
Inst php-php-gettext (1.0.12-0.1 Ubuntu:18.04/bionic [all])
Inst php-phpseclib (2.0.9-1 Ubuntu:18.04/bionic [all])
Inst php7.2-snmp (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst php-snmp (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Inst php-twig (2.4.6-1 Ubuntu:18.04/bionic [all])
Inst snmp (5.7.3+dfsg-1.8ubuntu3.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Inst libjs-jquery-ui-touch-punch (0.0~git20141218.2.4bc0091+dfsg1-2 Ubuntu:18.04/bionic [all])
Inst rrdtool (1.7.0-1build1 Ubuntu:18.04/bionic [amd64])
Inst cacti (1.1.38+ds1-1 Ubuntu:18.04/bionic [all])
Inst cacti-spine (1.1.35-1 Ubuntu:18.04/bionic [amd64])
Conf libapr1 (1.6.3-2 Ubuntu:18.04/bionic [amd64])
Conf libaprutil1 (1.6.1-2 Ubuntu:18.04/bionic [amd64])
Conf libaprutil1-dbd-sqlite3 (1.6.1-2 Ubuntu:18.04/bionic [amd64])
Conf libaprutil1-ldap (1.6.1-2 Ubuntu:18.04/bionic [amd64])
Conf apache2-bin (2.4.29-1ubuntu4.5 Ubuntu:18.04/bionic-proposed [amd64])
Conf apache2-utils (2.4.29-1ubuntu4.5 Ubuntu:18.04/bionic-proposed [amd64])
Conf apache2-data (2.4.29-1ubuntu4.5 Ubuntu:18.04/bionic-proposed [all])
Conf apache2 (2.4.29-1ubuntu4.5 Ubuntu:18.04/bionic-proposed [amd64])
Conf libaio1 (0.3.110-5 Ubuntu:18.04/bionic [amd64])
Conf mysql-client-core-5.7 (5.7.24-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf mysql-client-5.7 (5.7.24-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf mysql-server-core-5.7 (5.7.24-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf libevent-core-2.1-6 (2.1.8-stable-4build1 Ubuntu:18.04/bionic [amd64])
Conf mysql-server-5.7 (5.7.24-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf libjs-jquery-hotkeys (0~20130707+git2d51e3a9+dfsg-2ubuntu1 Ubuntu:18.04/bionic [all])
Conf dbconfig-common (2.0.9 Ubuntu:18.04/bionic [all])
Conf default-mysql-client (1.0.4 Ubuntu:18.04/bionic [all])
Conf dbconfig-mysql (2.0.9 Ubuntu:18.04/bionic [all])
Conf default-mysql-server (1.0.4 Ubuntu:18.04/bionic [all])
Conf fonts-dejavu-extra (2.37-1 Ubuntu:18.04/bionic [all])
Conf fonts-font-awesome (4.7.0~dfsg-3 Ubuntu:18.04/bionic [all])
Conf php-common (1:60ubuntu1 Ubuntu:18.04/bionic [all])
Conf php7.2-common (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php7.2-json (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php7.2-opcache (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php7.2-readline (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php7.2-cli (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf libapache2-mod-php7.2 (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf libapache2-mod-php (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Conf libdbi1 (0.9.0-5 Ubuntu:18.04/bionic [amd64])
Conf libhtml-template-perl (2.97-1 Ubuntu:18.04/bionic [all])
Conf libjs-d3 (3.5.17-2 Ubuntu:18.04/bionic [all])
Conf libjs-c3 (0.4.11+dfsg-2 Ubuntu:18.04/bionic [all])
Conf libjs-chartjs (1.0.2-1 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-ui (1.12.1+dfsg-5 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-colorpicker (1.2.16-1 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-cookie (12-1 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-jstree (3.3.5+dfsg1-1 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-metadata (12-1 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-tablesorter (1:2.29.5+dfsg1-1 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-timepicker (1.2-1 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-ui-theme-smoothness (1.12.1+dfsg-1 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-ui-theme-south-street (1.12.1+dfsg-1 Ubuntu:18.04/bionic [all])
Conf libjs-jquery-ui-theme-ui-darkness (1.12.1+dfsg-1 Ubuntu:18.04/bionic [all])
Conf libphp-phpmailer (5.2.14+dfsg-2.3 Ubuntu:18.04/bionic [all])
Conf librrd8 (1.7.0-1build1 Ubuntu:18.04/bionic [amd64])
Conf php7.2-gd (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php-gd (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Conf php7.2-gmp (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php-gmp (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Conf php7.2-ldap (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php-ldap (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Conf php7.2-mbstring (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php-mbstring (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Conf php7.2-mysql (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php-mysql (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Conf php7.2-xml (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php-xml (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Conf php-pear (1:1.10.5+submodules+notgz-1ubuntu1 Ubuntu:18.04/bionic [all])
Conf php-php-gettext (1.0.12-0.1 Ubuntu:18.04/bionic [all])
Conf php-phpseclib (2.0.9-1 Ubuntu:18.04/bionic [all])
Conf php7.2-snmp (7.2.10-0ubuntu0.18.04.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf php-snmp (1:7.2+60ubuntu1 Ubuntu:18.04/bionic [all])
Conf php-twig (2.4.6-1 Ubuntu:18.04/bionic [all])
Conf snmp (5.7.3+dfsg-1.8ubuntu3.1 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf libjs-jquery-ui-touch-punch (0.0~git20141218.2.4bc0091+dfsg1-2 Ubuntu:18.04/bionic [all])
Conf rrdtool (1.7.0-1build1 Ubuntu:18.04/bionic [amd64])
Conf cacti (1.1.38+ds1-1 Ubuntu:18.04/bionic [all])
Conf cacti-spine (1.1.35-1 Ubuntu:18.04/bionic [amd64])
```

---

### Post by pangilinan on 2018-11-25
root@cacti:/home/test# cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main





I try installing with apt.

root@cacti:/home/test# apt-get install mysql-server-5.7
Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-server-5.7 is already the newest version (5.7.24-0ubuntu0.18.04.1).
mysql-server-5.7 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


root@cacti:/home/test# apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
apache2 is already the newest version (2.4.29-1ubuntu4.4).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@cacti:/home/test#


root@cacti:/home/test# apt-get install libapache2-mod-php
Reading package lists... Done
Building dependency tree
Reading state information... Done
libapache2-mod-php is already the newest version (1:7.2+60ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@cacti:/home/test#

---

### Post by pangilinan on 2018-11-25
Also i tried to directly install cacti [COLOR=#000000][I] using this command here what i "get sudo apt -s install cacti-spine"

[/I][/COLOR]The following packages have unmet dependencies:
 cacti-spine : Depends: cacti (>= 0.8.6c) but it is not going to be installed
               Depends: libmysqlclient18 (>= 5.5.13-1) but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by oldos2er on 2018-11-25
If you are really running 18.04: It's not unusual for bad things to happen when you have repositories for two different Ubuntu versions.

---

### Post by deadflowr on 2018-11-25
Run
```
sudo apt edit-sources
```
This will open up the sources.list file.
Go down the the line
```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe

```and change it to
```
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
```
(add the # symbol to the front of the line)
then save it.

(the editor is whatever editor you set, so if Ubuntu's default then nano, if you change the editor to another such as vi then that's the editor.
For nano at least, to save press ctrl +X then select Y for yes then review the location is good and click enter and it'll save it and return to the normal prompt screen.
Typically if you've made no changes to where the file is located then just go ctrl+X > Y > Enter, done.
Then run 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt clean
sudo apt update
sudo apt install -f
```

To understand these commands

The first command clears out the old package listing information.
Do this so that no trusty package lists remain.

Then second command clears the archive packages out, so it to clears out any lingering trusty packages.
Probably not totally necessary, but doesn't hurt to cover all bases.

The third command refreshes the package lists, clean.

And the fourth command attempts to fix the broken package issues.

Post back results, please.

---

### Post by pangilinan on 2018-11-25
root@cacti:/home/test# nano /etc/apt/sources.list


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security main
**#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe **   <- added #
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main



root@cacti:/home/test# **sudo rm -rf /var/lib/apt/lists/***
root@cacti:/home/test# **sudo apt clean**
root@cacti:/home/test# **sudo apt update**
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease [242 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main amd64 Packages [1,019 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main Translation-en [516 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [207 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security/main Translation-en [81.5 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [442 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [166 kB]
Fetched 2,847 kB in 5s (622 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
root@cacti:/home/test#** sudo apt install -f**
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@cacti:/home/test#

Nothing installed...


root@cacti:/home/test# **apt-get install cacti cacti-spine <- then i run cacti installer**
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package cacti
E: Unable to locate package cacti-spine
root@cacti:/home/test# nano /etc/apt/sources.list

---

### Post by oldos2er on 2018-11-25
You apparently don't have the universe repository enabled? That's where both cacti and cacti-spine are.

[https://packages.ubuntu.com/search?keywords=cacti&searchon=names&suite=bionic&section=all](https://packages.ubuntu.com/search?keywords=cacti&searchon=names&suite=bionic&section=all)

---

### Post by deadflowr on 2018-11-25
Indeed, no bionic universe enabled. Sorry I missed it.
So now you run this add-apt command to enable it properly
```
sudo add-apt-repository universe
sudo apt update
sudo apt install cacti cacti-spine
```
but actually you only really need to install cacti-spine, as cacti will get pulled in with that automatically.

---

### Post by pangilinan on 2018-11-26
thanks for the help  was able to install it successfully.

---

