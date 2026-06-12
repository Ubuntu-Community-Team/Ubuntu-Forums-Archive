---
title: "Set up a server with DTC Control panel"
date: 2006-09-10
forum: Outdated Tutorials &amp; Tips
---

### Post by kdavies on 2006-09-10
Ubuntu 6.06 LTS ISP Server set up with DTC

Install of Ubuntu 6.06 LTS Server with the DTC control panel to provide a secure virtual hosting platform for Email, Webmail Anti-spam and Anti-virus with usage statistics.
This system uses the LAMP install of Ubuntu and Domain Technologies control panel.

Remote access with ssh
Firewall security with Shorelines Shorewall
DNS Sever: Bind9
FTP server: Pureftp
Mail: Postfix, Courier POP(s), IMAP(s)
Web mail with Squirrelmail
Mailing lists management with mlmmj
Anti virus and Spam controls with Spam Assassin, Clam AV,SPF, Amavis
Web statistics with Webalizer and awstats
Security certificates from CaCerts

The control panel also features a package installer for 'one click' application deployment.
For the future, the control panel supports virtualisation with xen.

Install the Ubuntu LAMP server.

Reconfigure eth0 for a static ip address.

In this example I used 192.168.1.15 as the server ip.

Now for some configuration changes as root.

sudo -i

vi /etc/network/interfaces

#This file describes the network interfaces available on your system
#and how to activate them. For more information, see interfaces(5). 
#The loopback network interface
auto lo

iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet 
   static address
	192.168.1.15
	netmask 255.255.255.0
	network
	192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1


Turn off IPv6

echo "alias net-pf-10 off" > /etc/modprobe.d/bad_list

reload the network settings

/etc/init.d/networking restart

edit the /etc/hosts file to reflect the new ip.

vi /etc/hosts

127.0.0.1 localhost
192.168.1.15 myhostname.home.net myhostname
#The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

A reboot may be desirable at this stage.

Update your system

Check /etc/apt/sources.list to ensure repositories are enabled and remove cdrom from sources.list

vi /etc/apt/sources.list

apt-get update

apt-get upgrade
Remote access with ssh

apt-get install ssh

use ssh to connect to your server.

ssh adminname@192.168.1.15

To log into the admin account on the server without having to enter a password each time, populate the authorized_keys file on the server

ssh-copy-id -i ~/.ssh/id_dsa.pub adminname@192.168.1.15

You can now logon to the server.

ssh adminame@192.168.1.15

Start a root session

sudo -i

Remove some unwanted software

apt-get remove pppoeconf ppp pppconfig

Now to get some software

apt-get install screen defoma fontconfig gawk fileutils unrar-free zip unzip libzzip-0-12 mhonarc fakeroot chrootuid patch ucf openntpd ncftp

apt-get install php5 php5-cli php5-cgi php5-curl php5-gd php5-imap php5-mcrypt php5-mhash php5-pspell php5-recode php5-snmp php5-xmlrpc php5-xsl php-pear php-net-smtp php-net-socket php-xml-parser

When asked about libclient answer no. we want to use maildirs.

apt-get install bind9 bindgraph

apt-get install rrdtool rrdcollect mrtg-rrd librrd2 mrtg libgd-tools mrtg-contrib

Answer no to MRTG user only.
edit mrtg.conf to reflect your web work directory

vi /etc/mrtg.conf

apt-get install libmysqlclient12 libdigest-hmac-perl libdigest-sha1-perl libhtml-parser-perl libhtml-tagset-perl libltdl3 liburi-perl libnet-ip-perl libnet-dns-perl libnet-cidr-lite-perl libmail-spf-query-perl

apt-get install libsocket6-perl

needed for mysql authentication

apt-get install libpam-mysql libnss-mysql

apt-get install postfix postfix-mysql courier-base courier-pop courier-imap courier-authdaemon courier-maildrop courier-authmysql courier-ssl courier-imap-ssl courier-pop-ssl sasl2-bin libsasl2 libsasl2-module

rm /var/spool/postfix/var/run/saslauthd/
ln -s /var/run/saslauthd /var/spool/postfix/var/run

Answer yes for web based configuration files.
Chose Internet site

apt-get install spamassassin spamc

apt-get install clamav-base clamav-daemon php5-clamavlib clamav clamav-freshclam

apt-get install phpmyadmin webalizer awstats squirrelmail sqwebmail amavisd-new amavisd-new-milter

Had some problems with ftp-server, this worked.

aptitude -t ftp-server install pure-ftpd pure-ftpd-common pure-ftpd-mysql

pear install Crypt_CBC Auth_SASL

Some setting up

ln -s /usr/share/php/PEAR /usr/share/pear
ln -s /var/log /etc/apache2/logs
touch /etc/apache2/logs/mod_log_sql-preserve
chown nobody:nogroup /etc/apache2/logs/mod_log_sql-preserve

Set up root user password for MySQL

mysqladmin password mysqlrootpassword

PHP settings

Edit php.ini files.

vi /etc/php5/apache2/php.ini

set max_execution_time = 300
set memory_limit = 32M
set upload_max_filesize = 6M
set extension=mysql.so
set extension=mysqli.so

then copy to the cgi and cli directories

cp /etc/php5/apache2/php.ini /etc/php5/cgi
cp /etc/php5/apache2/php.ini /etc/php5/cli

Apache configuration

copy the cgi-bin alias from default site to apache2.conf

vi /etc/apache2/apache2.conf

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<"Directory "/usr/lib/cgi-bin">
	AllowOverride None
	Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
	Order allow,deny
	Allow from all
	
<"/Directory>

Restart Apache webserver

apache2ctl restart

Add the dtc repository to /etc/apt/sources.list

echo deb [ftp://ftp.gplhost.com/debian](ftp://ftp.gplhost.com/debian) stable main /etc/apt/sources.list

Update apt

apt-get update

apt-get install mlmmj sbox-dtc libapache2-mod-log-sql-mysql libapache2-mod-log-sql libapache2-mod-log-sql-ssl
Install DTC control panel

For the standard release:

apt-get dtc

For the latest version from cvs:

apt-get install cvs

cvs -d :pserver:anonymous@gplhost.com:/var/lib/cvs login

Password is anoncvs

cvs -d :pserver:anonymous@gplhost.com:/var/lib/cvs checkout dtc

cvs -d :pserver:anonymous@gplhost.com:/var/lib/cvs logout

Now to make DTC package

cd dtc/bin

./makeDebian

Next install the control panel

dpkg -i dtc_0.21.0-0_all.deb

To remove dtc

dpkg -r dtc

To reconfigure dtc

dpkg-reconfigure dtc

Install some traffic loggers

apt-get install mysqmail-postfix-logger mysqmail-courier-logger mysqmail-pure-ftpd-logger

Firewall configuration with Shorewall

apt-get install shorewall

To get phpmyadmin to work I had to edit /etc/phpmyadmin/blowfish_secret.inc.php and add it to /usr/share/phpmyadmin/config.inc.php

Using the control panel

Browse to [http://yourdtcdomain.com/dtcadmin](http://yourdtcdomain.com/dtcadmin)

Log in

Select DTC general configuration
Set Use SSL to yes

Using DTC

Set up mail

Select Users Administration ==>dtcdomain ==>Mailboxes

In the login box enter postmaster

Enter a password

for the postmaster username

In the Catch-all dropdown box select postmaster

Select ok

Continue to add emails.

To change account settings select
Admin editor or
Domain config

Adding a database

Select Client interface ==> database

First create a database username with a password

Select create

Create your database with username ==> create

---

### Post by coastdweller on 2006-09-10
This is very cool, thank you.

I'm running into some basic problems

I'll list them as I hit them.

Ubuntu 6.06 LTS Server (Dapper Drake)

1) When editing with VI interfaces I've no way to save the edits, then when I edit it with pico and attempt to restart networking it complains about:

> sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                         /etc/network/interfaces:10: too few parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:10: too few parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"

My file:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet
static address
192.168.0.99
netmask 255.255.255.0
network
192.168.0.4
broadcast 192.168.0.255
gateway 192.168.0.4


2) When installing the first software line:

> apt-get install screen defoma fontconfig gawk fileutils unrar-free zip unzip libzzip-0-12 mhonarc fakeroot chrootuid patch ucf openntpd ncftp
Reading package lists... Done
Building dependency tree... Done
Note, selecting coreutils instead of fileutils
coreutils is already the newest version.
E: Couldn't find package unrar-free

3) When installing the second software line:

> apt-get install php5 php5-cli php5-cgi php5-curl php5-gd php5-imap php5-mcrypt php5-mhash php5-pspell php5-recode php5-snmp php5-xmlrpc php5-xsl php-pear php-net-smtp php-net-socket php-xml-parser
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php5-imap

I'm thinking my sources might have something to do with this but not sure.

---

### Post by volksman on 2006-09-13
First, credit should be given to the original author at Howtoforge for this article.

Second your problems are common.  I believe that this article is flawe din a number of places.

As for your interfaces problem:
> auto eth0
iface eth0 inet static 
address 192.168.0.99
netmask 255.255.255.0
network 192.168.0.4
broadcast 192.168.0.255
gateway 192.168.0.4

If that doesn't work try removing the word static.  I forget exactly how I fixed it.

Further to that make sure you have the universe repo added to your sources.  May get you a little farther.

I tried this howto a few days ago on a fresh install of Ubuntu Server LAMP and it failed to work.  Moved on to try VHCS but there is no support (for the last 6 months), their site is down and there are reports of a fairly major flaw in the design.  Next test:  zpanel.

---

### Post by volksman on 2006-09-13
Hahahah....ok...kdavies is the orig author or is pretending to be... :)  My apologies if its the former...!

kdavies are you available on this forum for help with your guide?  I'd like to get it setup but there are some problems with your guide I'm not sure how to overcome.  I'd be willing to give it another shot and let you know where it fails me though... :)

---

### Post by volksman on 2006-09-17
The above is completely false!  I have been working on getting DTC to install for over a week now and after posting a note into their forums it appears that if you choose to go current and use Apache2 you will need to compile stuff to make it work.

This is not nearly as easy to install as kdavies is trying to make it out to be.

---

### Post by jbszulc on 2007-01-18
Does anyone know how to completely remove DTC and all of the things it has done to post fix courier apache2 etc? I really don't want to have to re-install.

---

### Post by altonbr on 2008-02-18
It would be cool to have this updated for Ubuntu 7.10/8.04 as it is now in the repositories.

---

### Post by johskar on 2008-05-09
> **altonbr said:**
> It would be cool to have this updated for Ubuntu 7.10/8.04 as it is now in the repositories.

yes indeed, specialy since I keep getting errors when running the /usr/share/dtc/admin/install/install
then I get
```
Creating chroot shell script...
-> Fixup rights
-> Managing ldconfig
exec: 17: /sbin/ldconfig.real: not found

```
Running 8.04 LTS

---

### Post by altonbr on 2008-05-09
> **johskar said:**
> yes indeed, specialy since I keep getting errors when running the /usr/share/dtc/admin/install/install
then I get
```
Creating chroot shell script...
-> Fixup rights
-> Managing ldconfig
exec: 17: /sbin/ldconfig.real: not found

```
Running 8.04 LTS

Damn. Try posting a bug at [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu)!

---

