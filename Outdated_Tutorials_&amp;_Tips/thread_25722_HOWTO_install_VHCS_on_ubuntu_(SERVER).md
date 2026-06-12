---
title: "HOWTO: install VHCS on ubuntu (SERVER)"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2005-04-10
Hello,
**Q.what is VHCS?**
[vhcs](http://www.vhcs.net) (Virtual Hosting Control System) is a software solution to run a webserver, mailserver, DNSserver, FTP server on linux (the current supported OS for now)

**Q.How to install it**
Just follow the TUTOrial below:

First begin by instaling ubuntu (don't need to choose server option, i will give you solutions to tweak it also).. after ubuntu is installed, Do the following:

Now you have the solution to either install it manually by following the silver text down there or follow the automatic method below:
```

wget http://www.siemens-mobiles.org/vhcs/vhcs.sh

```

now type
```

sudo sh vhcs.sh

```

and follow the inline instructions

[COLOR=Red]
NOTE: You are not authorised to modify/remove the license that is inside the script 3 times, it's 15 line and must be always the same 15 line, but you can modify the script and/or redestribute it without changing those licence lines, thank you[/COLOR]

[COLOR=Silver]0. make sure you have all needed repository, tested with /etc/apt/sources.list
```

deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse

```

1-making temp directories (you can change them to anything but we just need a folder to drop the files in it to make vhcs)
```

sudo mkdir /root/vhcs_tmp
sudo mkdir /root/vhcs_tmp/install
cd /root/vhcs_tmp/install

```

2- we update the current installed system 
```

sudo apt-get update

sudo apt-get upgrade -y

```


3-removing some uneeded packages, which can also cause the system not to function properly
```

sudo apt-get remove  -y lpr nfs-common portmap pidentd pcmcia-cs pppoe pppoeconf ppp pppconfig

```

4-removing some service from /etc/inetd.conf file
```

sudo update-inetd --remove daytime
sudo update-inetd --remove telnet
sudo update-inetd --remove time
sudo update-inetd --remove finger
sudo update-inetd --remove talk
sudo update-inetd --remove ntalk
sudo update-inetd --remove ftp
sudo update-inetd --remove discard

```

5-installing all needed packages
```

sudo apt-get install -y ssh postfix postfix-tls proftpd-mysql courier-authdaemon courier-base courier-imap courier-maildrop courier-pop libberkeleydb-perl libcrypt-blowfish-perl libcrypt-cbc-perl libcrypt-passwdmd5-perl libdate-calc-perl libdate-manip-perl libmime-base64-perl libdbd-mysql-perl libdbi-perl libio-stringy-perl libmail-sendmail-perl libmailtools-perl libmd5-perl libmime-perl libnet-dns-perl libnet-netmask-perl libnet-perl libnet-smtp-server-perl libperl5.8 libsnmp-session-perl libterm-readkey-perl libtimedate-perl perl perl-base perl-modules bind9 diff gzip iptables libmcrypt4 mysql-client mysql-common mysql-server patch php4 php4-mcrypt php4-mysql php4-pear procmail tar original-awk libterm-readpassword-perl libsasl2-modules libsasl2 sasl2-bin apache2 apache2-common apache2-mpm-prefork libapache2-mod-php4 bzip2


```

6-getting vhcs archive file from vhcs.net (this is for the current 2.4 beta version, visit [http://www.vhcs.net](http://www.vhcs.net) for the current/latest version)
```

sudo wget http://puzzle.dl.sourceforge.net/sourceforge/vhcs/vhcs2.4.tar.bz2

```

7-exctracting the archive, and entering into the vhcs sources directory
```

sudo bunzip2 vhcs2.4.tar.bz2
sudo tar -xvvf vhcs2.4.tar
cd ./vhcs-2.4


```

8-installing the vhcs
8.1-make install vhcs which will put all the file into /tmp/vhcs2 folder
```

sudo make install

```

8.2-copying all the files into their real directory
```

sudo cp -R /tmp/vhcs2/etc/* /etc
sudo cp -R /tmp/vhcs2/var/* /var
sudo cp -R /tmp/vhcs2/usr/* /usr

```

**ok now vhcs files are in place, we proceed to the configuration now,**

9-so first we change/create the mysql root password
```

mysqladmin -u root -p password "new password here"

```

10-after the vhcs has been installed, and the mysql root has been changed let's make sure we are in the latest packages
```

sudo apt-get update

sudo apt-get upgrade -y

sudo apt-get clean


```

11-ok, this is the time to make vhcs installed and fully operational,
```

sudo /var/www/vhcs2/engine/setup/vhcs2-setup

```
here you will be asked about passwords, ip etc... it's recommanded that you use private ip of the server

12-VHCS installed, now you need to include the apache configuration file and to restart apache
so open /etc/apache2/httpd.conf
```

sudo pico /etc/apache2/httpd.conf

```
and append the following instruction at the end of the file
```

Include /etc/apache2/sites-available/vhcs2.conf

```
restart apache
```

/etc/init.d/apache2 restart

```


13-finally we add the daemon to boot on ubuntu startup
```

sudo update-rc.d vhcs2_daemon defaults

sudo update-rc.d vhcs2_network defaults

```
[/COLOR]


now visit [http://whatever.the.servers.ip.is/vhcs2/](http://whatever.the.servers.ip.is/vhcs2/) or [http://127.0.0.1/vhcs2/](http://127.0.0.1/vhcs2/) and begin by creating a reseller, then a hosting template to add a domain

**F.A.Q**
**Q.How to make ubuntu start without X server, to have more free RAM**
from a terminal remove gdm, xdm and kdm (normally only gdm is installed but just to make sure)
```

sudo apt-get remove gdm
sudo apt-get remove xdm
sudo apt-get remove kdm

```

**Q.How to make it possible that the user use .htaccess file (normally can't be used, give ERROR 500)**
edit /etc/vhcs2/apache/working/vhcs2.conf file
search for in the domain you need to give the rights to use .htaccess file
```

AllowOverride AuthConfig

```

replace with
```

AllowOverride All

```

replace the file /etc/apache2/sites-available/vhcs2.conf with this one
```

sudo cp /etc/vhcs2/apache/working/vhcs2.conf /etc/apache2/sites-available/vhcs2.conf

```

restart apache2
```

sudo /etc/init.d/apache2 restart

```

**Q.is it possible to make it by default .htaccess can be used**
Yes. Open /etc/vhcs2/apache/parts/{prefix}_entry.tpl where {prefix} is "als" and "dmn" and "sub" without quotes
search for
```

AllowOverride AuthConfig

```

replace with
```

AllowOverride All

```

edit also /etc/vhcs2/apache/working/vhcs2.conf to enable it for the current registered domains
replace all occurences of:
```

AllowOverride AuthConfig

```

with
```

AllowOverride All

```

copy this file to /etc/apache2/sites-available/
```

sudo cp /etc/vhcs2/apache/working/vhcs2.conf /etc/apache2/sites-available/vhcs2.conf

```

restart apache2
```

sudo /etc/init.d/apache2 restart

```

**Q.mysql root password is stored in /etc/proftpd.conf in clear text, can i hide it?**
you can only hide it from normal users, but unfortunately it will be always visibe to sudoers users
```

sudo chmod 0600 /etc/proftpd.conf

```

**Q.how to change mysql password**
changing the mysql root passwors is easy, just follow this four steps
1. begin by changing the mysql root password with
```

mysqladmin -u root -p password "new password here"

```

2. go to /var/www/vhcs2/engine and execute vhcs2-db-password
```

cd /var/www/vhcs2/engine
sudo ./vhcs2-db-password

```
follow the screen instructions,

3. go to /etc open proftpd.conf and change password there
```

sudo pico /etc/proftpd.conf

```
search for (Ctrl + W to search with pico)
```

vhcs2@localhost

```
you will find after it root and your old mysql password so update the password.

4. restart proftpd
```

/etc/init.d/proftpd restart

```

that's it :D

--== new questions will be added later also keep checking this topic ==--

**Troublesshooting**

**Q.When i run /var/www/vhcs2/engine/setup/vhcs2-setup file, i get errors something about mysql error**
this error has occured because your mysql password contains non alpha-numeric charachters, this can be solved by editing /var/www/vhcs2/engine/setup/vhcs2-setup, so:
```

sudo pico /var/www/vhcs2/engine/setup/vhcs2-setup

```
Ctrl + w to search, type "setup_sql" without quotes
go down and find the line
```

    my $cmd = "$main::cfg{'CMD_MYSQL'} --user=$main::db_user --pass=$main::db_pwd < /tmp/db.sql 1>/tmp/db.sql.stdout 2>/tmp/db.sql.stderr";

```

replace in it 
```

--pass=$main::db_pwd

```

with 
```

--pass=\"$main::db_pwd\"

```

so it will look like this
```

    my $cmd = "$main::cfg{'CMD_MYSQL'} --user=$main::db_user --pass=\"$main::db_pwd\" < /tmp/db.sql 1>/tmp/db.sql.stdout 2>/tmp/db.sql.stderr";

```
run /var/www/vhcs2/engine/setup/vhcs2-setup again


**Q.my ips are resolving private to the outside (dnsreport.com report private ips instead of public ones)**
There's two methods to solve this problem, i will state one now, the second one will be added later

this method consist of reinstalling VHCS with public IP, and solve apache resolving problem (when public ip is used, apache will no longer resolve domains)
first you need to remove all added users (go to vhcs2 database in mysql and see the uid in admin table)
```

sudo userdel vu200X

```
where X is the user number (vhcs2 will begin with 1)

remove the added groups
```

sudo groupdel vu200X

```
where X is the group number (vhcs2 will begin with 1)

remove the working conf files
```

sudo rm /etc/vhcs2/apache/working/vhcs2.conf
sudo rm /etc/vhcs2/bind/working/*
sudo rm /etc/apache2/sites-available/vhcs2.conf
sudo rm /var/cache/bind/*

```

now you're ready to install, repeat only step 11 but use public ip this time

now proceed to edit the apache files to resolve correctly
Open /etc/vhcs2/apache/parts/{prefix}_entry.tpl where {prefix} is "als" and "dmn" and "sub" without quotes
replace
```

<VirtualHost {DMN_NAME}>

```
with
```

<VirtualHost *>

```

recreate reseller, etc... now

**Q.FTP always give authetifications incorrect!!!**
```

sudo pico /etc/proftpd.conf

```

search for
```

SQLConnectInfo          vhcs2@localhost root

```

mysql root password must be in clear text right after root in the aboce text, if not add it and
```

sudo /etc/init.d/proftpd restart

```




Any suggestion about a step, or any question to be added to the F.A.Q/Troubleshooting is appreciated
Thanks to alexkotov, BeeEmm, Ico Dimov, Dimitri Tarassenko, Nigel Jones, Markus Petzsch, Tassoman, developpers of [VHCS open source project](http://sourceforge.net/projects/vhcs/)

[COLOR=SlateGray]
Version History
------------------------
Version [ Date ] Changes
--------------------------------------
1.0 [ 11-04-2005 ] First Version
1.1 [ 26-04-2005 ] Fix the Apache error when fixing resolving, fix a typo mistakes...
1.2 [ 26-04-2005 ] Added the mysql root password changing
1.3 [ 02-05-2005 ] Added repository reminder
1.4 [ 08-05-2005 ] Added the automatic installation script
[/COLOR]

---

### Post by Pablo on 2005-04-11
great HOWTO! but 
After 5 stage, 

postfix-tls is already the newest version.
_E: Couldn't find package proftpd-mysql_

I use new ubuntu, new instalation 
how to fix this problem?

---

### Post by Gandalf on 2005-04-11
[QUOTE=Pablo]great HOWTO! but 
After 5 stage, 

postfix-tls is already the newest version.
_E: Couldn't find package proftpd-mysql_

I use new ubuntu, new instalation 
how to fix this problem?[/QUOTE]
 did you [add extra repositories](http://ubuntuguide.org/#extrarepositories)?

---

### Post by Francisco on 2005-04-16
Hi,

 on [http://127.0.0.1/vhcs2/gui/](http://127.0.0.1/vhcs2/gui/) I get this error:


Fatal error: Call to undefined function: mcrypt_module_open() in /var/www/vhcs2/gui/include/vhcs-config.php on line 10

---

### Post by zybrid on 2005-04-24
Hi, i look forward to get VHCS up and running, but i got some errors on step 11.

zybrid@zybrid:/root/vhcs_tmp/install/vhcs-2.4$ sudo /var/www/vhcs2/engine/setup/vhcs2-setup

CRITICAL ERROR: Module [MIME::Entity] WAS NOT FOUND !

CRITICAL ERROR: Module [MIME::Parser] WAS NOT FOUND !

CRITICAL ERROR: Module [Crypt::CBC] WAS NOT FOUND !

CRITICAL ERROR: Module [Crypt::Blowfish] WAS NOT FOUND !

CRITICAL ERROR: Module [Term::ReadPassword] WAS NOT FOUND !

Modules [MIME::Entity, MIME::Parser, Crypt::CBC, Crypt::Blowfish, Term::ReadPassword] WAS NOT FOUND in your system...

With synaptic i can install Blowfish CBC and ReadPassword, But not Entity and parser. which packages should i install?

---

### Post by zybrid on 2005-04-24
[QUOTE=zybrid]Hi, i look forward to get VHCS up and running, but i got some errors on step 11.

zybrid@zybrid:/root/vhcs_tmp/install/vhcs-2.4$ sudo /var/www/vhcs2/engine/setup/vhcs2-setup

CRITICAL ERROR: Module [MIME::Entity] WAS NOT FOUND !

CRITICAL ERROR: Module [MIME::Parser] WAS NOT FOUND !

CRITICAL ERROR: Module [Crypt::CBC] WAS NOT FOUND !

CRITICAL ERROR: Module [Crypt::Blowfish] WAS NOT FOUND !

CRITICAL ERROR: Module [Term::ReadPassword] WAS NOT FOUND !

Modules [MIME::Entity, MIME::Parser, Crypt::CBC, Crypt::Blowfish, Term::ReadPassword] WAS NOT FOUND in your system...

With synaptic i can install Blowfish CBC and ReadPassword, But not Entity and parser. which packages should i install?[/QUOTE]

The solution were to install libmime-pearl 
Later i got a problem with bind, so i needed to install bind. now everything works fine.
thanks!

---

### Post by Gandalf on 2005-04-25
guys, are you sure you installed exacly how i describe it? i mean for packages??? because i installed till now 15 ubuntu server, none had a problem!

---

### Post by steffen on 2005-04-25
Seriously guys! A quick look at [www.vhcs.sf.net](www.vhcs.sf.net) - this system looks awesome? Why haven't I heard of it before? It's open source, and the GUI is PHP as well. It looks as the perfect system!

Thanks for the howto - and thanks for the tip! I'll definitely try this out, and probably merge my servers to VHCS as soon as possible!

I see it wasn't launched under an OSI license until August 2004, because the former marketing strategy didn't work. Anyway - this looks too good to be true, and the initiative seems to be worth both using and supporting!

Thanks again!!! :grin:

---

### Post by Gandalf on 2005-04-25
[QUOTE=steffen]Seriously guys! A quick look at [www.vhcs.sf.net](www.vhcs.sf.net) - this system looks awesome? Why haven't I heard of it before? It's open source, and the GUI is PHP as well. It looks as the perfect system!

Thanks for the howto - and thanks for the tip! I'll definitely try this out, and probably merge my servers to VHCS as soon as possible!

I see it wasn't launched under an OSI license until August 2004, because the former marketing strategy didn't work. Anyway - this looks too good to be true, and the initiative seems to be worth both using and supporting!

Thanks again!!! :grin:[/QUOTE]
 no problem man, i'm using VHCS since 4 months already and works gr8, it has some lack of features compared to cpanel, but at least it's an open source project so i like it...

---

### Post by plpeyssard on 2005-05-07
High
Thank you for this wonderfull tutorial and this FAQ which works fine and help a lot.

I use vhcs 2.4 beta version build  03-2005-21
I have some trouble about **domain statistics.** It does not work. 
Everething is 0.00 B in reseller and user screen.

I discovered that the /etc/init.d/vhcs-network daemon did not start.
here is the log message:

bind: Address already in use
ll_daemon_start: Resource temporarily unavailable

Is there a way to find that adress and change it ?
What can i do to solve that situation ?

Thanks.

---

### Post by Gandalf on 2005-05-07
[QUOTE=plpeyssard]High
Thank you for this wonderfull tutorial and this FAQ which works fine and help a lot.

I use vhcs 2.4 beta version build  03-2005-21
I have some trouble about **domain statistics.** It does not work. 
Everething is 0.00 B in reseller and user screen.

I found nothing about that problem in Vhcs logs.
Maybe i forgot something ?

What is the track to solve that situation ?

Thanks.[/QUOTE]
 is apache resolving correctly???

---

### Post by Gandalf on 2005-05-07
HOWTO updated...

---

### Post by JesseSparks on 2005-05-08
Hey Gandalf,

I really like the post the install is great. I did the install before the script so I am trying a new install with the script. I want to say thank you for the great info. I run a small hosting company and the VHCS is great for my needs but I would like to make all VHCS functions to be behind SSL do you know how this is done. I have tried several things and none have worked yet.

Jesse Sparks.

---

### Post by Gandalf on 2005-05-08
[QUOTE=JesseSparks]Hey Gandalf,

I really like the post the install is great. I did the install before the script so I am trying a new install with the script. I want to say thank you for the great info. I run a small hosting company and the VHCS is great for my needs but I would like to make all VHCS functions to be behind SSL do you know how this is done. I have tried several things and none have worked yet.

Jesse Sparks.[/QUOTE]
 no sorry vhcs don't support SSL yet, i'm not a developper so :(
and no problem i hope the script will work

---

### Post by jayd36108 on 2005-05-08
ok gandalf, on the section of the install where it says we will change your mysql password, do i enter a new password?

cause if so i entered it then at the next screen it asked me if i changed the default root password, should i enter the password i typed in on the previous screen or hit enter?

---

### Post by Gandalf on 2005-05-08
[QUOTE=jayd36108]ok gandalf, on the section of the install where it says we will change your mysql password, do i enter a new password?

cause if so i entered it then at the next screen it asked me if i changed the default root password, should i enter the password i typed in on the previous screen or hit enter?[/QUOTE]
 well here it ask you about to change mysql password, on a fresh OS/Mysql installation you enter the password where it asks for it the first time and just hit enter the second time,
in other word it asks for
New password
Old password

old password on frsh install is nothing NADA...

---

### Post by jayd36108 on 2005-05-08
[QUOTE=Gandalf]well here it ask you about to change mysql password, on a fresh OS/Mysql installation you enter the password where it asks for it the first time and just hit enter the second time,
in other word it asks for
New password
Old password

old password on frsh install is nothing NADA...[/QUOTE]

ok so when i enter my password then at the next screen i just hit enter

---

### Post by Gandalf on 2005-05-08
[QUOTE=jayd36108]ok so when i enter my password then at the next screen i just hit enter[/QUOTE]
 exactly, should I explain it better in the script???

---

### Post by jayd36108 on 2005-05-08
[QUOTE=Gandalf]exactly, should I explain it better in the script???[/QUOTE]

yeah, it might help newbies like me, because that can be a little confusing when you get the point you enter your new password then hit enter at the next screen when it asks for the old password.

overall, it's a great script and worked flawlessly except for operator error on my half.

---

### Post by Gandalf on 2005-05-08
[QUOTE=jayd36108]yeah, it might help newbies like me, because that can be a little confusing when you get the point you enter your new password then hit enter at the next screen when it asks for the old password.

overall, it's a great script and worked flawlessly except for operator error on my half.[/QUOTE]
 ok i'll try to make it more clear,
please explain what do you mean by operator error??
thx

---

### Post by AlBundy on 2005-05-09
How can I write administrator's Email address because when I write I've got this message:

ERROR: Unable to connect SQL server

I try what You write in the troubleshoouting, but it doesn't work :(

---

### Post by Gandalf on 2005-05-09
[QUOTE=AlBundy]How can I write administrator's Email address because when I write I've got this message:

ERROR: Unable to connect SQL server

I try what You write in the troubleshoouting, but it doesn't work :([/QUOTE]
 try
mysql -u root -p
does it asks you for a password? if yes enter the password you choosed what happens?
this has nothing to do with admin mail because vhcs2 will install a database inside your mysql and must have access

---

### Post by AlBundy on 2005-05-09
[QUOTE=Gandalf]try
mysql -u root -p
does it asks you for a password? if yes enter the password you choosed what happens?
this has nothing to do with admin mail because vhcs2 will install a database inside your mysql and must have access[/QUOTE]

ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)

---

### Post by Infernal on 2005-05-09
i installed is succesfull, but how do i add a ftp and mail server??

---

### Post by Gandalf on 2005-05-09
[QUOTE=Infernal]i installed is succesfull, but how do i add a ftp and mail server??[/QUOTE]
 it is already installed, just add a reseller, create a package and a domain, inside the domain you will have Email and FTP accounts

---

### Post by Gandalf on 2005-05-09
[QUOTE=AlBundy]ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)[/QUOTE]
 well that means you are entering the wrong mysql password
google recover mysql root password (it is done by mysqlsafe)

---

### Post by Infernal on 2005-05-09
[QUOTE=Gandalf]it is already installed, just add a reseller, create a package and a domain, inside the domain you will have Email and FTP accounts[/QUOTE]

i created a reseller, created a package and a domain, then i go to manage domain and click on my domain, and see this: 

Domain name  	****
Domain IP 	****
Status 	ok
PHP support 	Enabled
CGI support 	Enabled
MySQL support 	Enabled
Traffic in MB 
0 B / 0 B
Disk in MB 	
0 B / 0 B
Feature 	Used 	Limit
Mail accounts 	0 	unlimited

FTP accounts 	0 	unlimited
SQL databases 	0 	unlimited
SQL users 	0 	unlimited
Subdomains 	0 	unlimited
Domain aliases 	0 	unlimited


but i can't add and ftp or mail account



*EDIT*

Never mind, already found it

---

### Post by Infernal on 2005-05-09
[QUOTE=Infernal]i created a reseller, created a package and a domain, then i go to manage domain and click on my domain, and see this: 

Domain name  	****
Domain IP 	****
Status 	ok
PHP support 	Enabled
CGI support 	Enabled
MySQL support 	Enabled
Traffic in MB 
0 B / 0 B
Disk in MB 	
0 B / 0 B
Feature 	Used 	Limit
Mail accounts 	0 	unlimited

FTP accounts 	0 	unlimited
SQL databases 	0 	unlimited
SQL users 	0 	unlimited
Subdomains 	0 	unlimited
Domain aliases 	0 	unlimited


but i can't add and ftp or mail account



*EDIT*

Never mind, already found it[/QUOTE]
 i have another question.it's about the domain. is the domain like [www.something.com](www.something.com) ???

i'm having a problem with the ip too. i have a thompson modem router, and my ip is a privat one,  like 10.0.0.XX . How do i redirect that to my public ip??

thx

---

### Post by AlBundy on 2005-05-09
When I restart apache2 I've got this error message:

httpd (pid 7741?) not running

---

### Post by AlBundy on 2005-05-09
[QUOTE=AlBundy]When I restart apache2 I've got this error message:

httpd (pid 7741?) not running[/QUOTE]

But I continue the Instalation and it's works  \\:D/   \\:D/   \\:D/   \\:D/   \\:D/   \\:D/

---

### Post by Infernal on 2005-05-10
is there a way to quicky remove vhcs???

---

### Post by Gandalf on 2005-05-11
yes,
run /var/www/vhcs2/engine/setup/vhcs2-uninstall

---

### Post by Gandalf on 2005-05-11
[QUOTE=Infernal]i have another question.it's about the domain. is the domain like [www.something.com](www.something.com) ???

i'm having a problem with the ip too. i have a thompson modem router, and my ip is a privat one,  like 10.0.0.XX . How do i redirect that to my public ip??

thx[/QUOTE]
 do you use local DNS or external DNS???

---

### Post by Infernal on 2005-05-11
[QUOTE=Gandalf]yes,
run /var/www/vhcs2/engine/setup/vhcs2-uninstall[/QUOTE]

i found the file, but how do i run it (me=noob)

---

### Post by gmagana on 2005-05-15
[QUOTE=Infernal]i found the file, but how do i run it (me=noob)[/QUOTE]

Just type this in the command line:
**/var/www/vhcs2/engine/setup/vhcs2-uninstall**

---

### Post by gmagana on 2005-05-16
Now I got a question myself:

I just went through the install using your script (BTW **THANKS**!!!!!!).  I ran into a couple bugs:

- When the script is running, on the step you labeled on your post as :

*5-installing all needed packages*
```
sudo apt-get install -y ssh postfix postfix-tls [....]
```

Some of the packages pop up confirmation windows (Proftpd to ask whether or not run as standaole, and Courier to as whether or not to use separate directories for config).  These windows are never visible and your script just seems to happily hang forever.  If may be wise to let this part of your script display the output, or at least warn the user to run a parallel "tail" of the script's log.

- The other thing is that apache2 seems to be confised as to the domain name of the machine, specially if you are installing with one single IP, you will run into problems as soon as you add tyhe first virtual host.  Is there a way to address this via your script?

---

### Post by Gandalf on 2005-05-16
[QUOTE=gmagana]Now I got a question myself:

I just went through the install using your script (BTW **THANKS**!!!!!!).  I ran into a couple bugs:

- When the script is running, on the step you labeled on your post as :

*5-installing all needed packages*
```
sudo apt-get install -y ssh postfix postfix-tls [....]
```

Some of the packages pop up confirmation windows (Proftpd to ask whether or not run as standaole, and Courier to as whether or not to use separate directories for config).  These windows are never visible and your script just seems to happily hang forever.  If may be wise to let this part of your script display the output, or at least warn the user to run a parallel "tail" of the script's log.

- The other thing is that apache2 seems to be confised as to the domain name of the machine, specially if you are installing with one single IP, you will run into problems as soon as you add tyhe first virtual host.  Is there a way to address this via your script?[/QUOTE]
 thanks man i think that's what explains why sometimes it hangs on some PCs thanks for bringing this at my attention i will try to see a workaround for it

about the apache thing well unfortunately it's a known unfixed bug of VHCS it says that can't determine nameserver using IP instead no??? if it's that i fix it by removing the NameVirtualHost IP and adding ServerName IP
i/we (if you want to help me with the script) can make a simple patch file for the  /etc/vhcs2/apache/parts/vh_entry.tpl file

---

### Post by Gandalf on 2005-05-19
Script updated,

changelog:
added the installation of VHCS 2.4.2 stable
added the upgrade from VHCS2.4 Beta to VHCS 2.4.2 stable
added a question on changing mysql root password
fixed some minor things....


thanks to all members for their support

---

### Post by Finchwizard on 2005-05-19
Does anyone have a copy of this new updated script.

The main site isn't working.

Cheers.

---

### Post by Gandalf on 2005-05-20
[QUOTE=Finchwizard]Does anyone have a copy of this new updated script.

The main site isn't working.

Cheers.[/QUOTE]
 sorry man, as i told you in PM, i was moving from debian sarge (vhcs2.4 beta) to ubuntu hoary(vhcs2.4 stable)

i fifnished in less than 3 hrs everything, and now it's working but sometimes you will notice a down time because in fact i have a lot more to do with NFS settings and etc... and i need to reboot sometimes

---

### Post by boosted on 2005-05-27
when I go here [http://192.168.1.100/vhcs2/](http://192.168.1.100/vhcs2/) I get a directory Listing with these directories: 
       27-May-2005 03:56      -  
[DIR] backups/                27-May-2005 04:02      -  
[DIR] daemon/                 27-May-2005 03:56      -  
[DIR] engine/                 27-May-2005 03:56      -  
[DIR] gui/                    27-May-2005 03:56      -  

if I click on gui  firefox ask me if I want to open the file or save it?????  file type is PHTML???   how do I get to the gui????

---

### Post by AlBundy on 2005-05-29
How can I upgrade VHCS from 2.2 to 2.4?

---

### Post by Gandalf on 2005-05-29
[QUOTE=AlBundy]How can I upgrade VHCS from 2.2 to 2.4?[/QUOTE]
 use the upgrade from 2.4Beta to 2.4Stable it is the same,
the only difference that is between 2.2 and 2.4 beta is the gui, but in 2.4Stable the engine has been changed too

---

### Post by AlBundy on 2005-05-29
[QUOTE=Gandalf]use the upgrade from 2.4Beta to 2.4Stable it is the same,
the only difference that is between 2.2 and 2.4 beta is the gui, but in 2.4Stable the engine has been changed too[/QUOTE]

OK, but how can I do It?

I running only the 2.4 install script?

---

### Post by zybrid on 2005-05-30
> Thanks again for this wonderful script!

How do i change settings on the mailserver?
I can´t find many settings in the admin/reseller-interface. 
In the configfiles it says that i shouldn´t edit the config-files manually.

For example i want to change the following:

* To increase the quota from 4 MB to 0 MB (infinitive)
* To send all email through my ISP SMTPserver

I want a big mean kickassing antispammachine also, any ideas?
Perhaps installing spamassassin and clamav is suffice?

Best Regards
Linus

In the following file i found some nice settings!

/var/www/vhcs2/gui/tools/webmail/inc/config.php
$quota_limit = 4096;  //  in KB, eg. 4096 Kb = 4MB

---

### Post by zybrid on 2005-05-30
[QUOTE=AlBundy]OK, but how can I do It?

I running only the 2.4 install script?[/QUOTE]

At the beginning in the script you should be able to choose upgrade from VHCS 2.2 to 2.4

---

### Post by AlBundy on 2005-05-30
[QUOTE=zybrid]At the beginning in the script you should be able to choose upgrade from VHCS 2.2 to 2.4[/QUOTE]

Thanks, It's works :)

---

### Post by zybrid on 2005-05-30
Hey you know what would be great in the script? 

The option to choose how the mail are going to be sent. 

Like for me i need to send all my mail through my ISP smtpserver and auth with username&password.  I haven´t fint any correct config for that yet. :/

---

### Post by CrustyDOD on 2005-06-02
Hey

i installed VHCS, ran: sudo /var/www/vhcs2/engine/setup/vhcs2-setup

entered data and after email i get this:

> ERROR: Unable to connect SQL server ! 

so did i enter password wrong? NO!
tried: mysql -u root -p and entered the same password and i can log in to mysql just fine..

So what's wrong with it??

PS: i tried about 8 times so i'm sure i entered the correct password!

Edit: should there be my password on setup screen: Please enter system SQL password (Enter for defaults) [none]:

also tried with empty and also doesn't work..

If i go to gui page i get this error, which is strange: Warning: mysql_connect(): Access denied for user: 'root@localhost' (Using password: NO) in /var/www/vhcs2/gui/include/adodb/drivers/adodb-mysql.inc.php on line 235

Using password: NO ?!?

Can i write mysql password manually into some config file or what, cause its clear the setup isn't saving/registering it no matter what i type..

---

### Post by Gandalf on 2005-06-03
[QUOTE=CrustyDOD]Hey

i installed VHCS, ran: sudo /var/www/vhcs2/engine/setup/vhcs2-setup

entered data and after email i get this:

 

so did i enter password wrong? NO!
tried: mysql -u root -p and entered the same password and i can log in to mysql just fine..

So what's wrong with it??

PS: i tried about 8 times so i'm sure i entered the correct password!

Edit: should there be my password on setup screen: Please enter system SQL password (Enter for defaults) [none]:

also tried with empty and also doesn't work..

If i go to gui page i get this error, which is strange: Warning: mysql_connect(): Access denied for user: 'root@localhost' (Using password: NO) in /var/www/vhcs2/gui/include/adodb/drivers/adodb-mysql.inc.php on line 235

Using password: NO ?!?

Can i write mysql password manually into some config file or what, cause its clear the setup isn't saving/registering it no matter what i type..[/QUOTE]
 if your password contain special characters like ; it's normal, as i said try only alpha-numeric characters

---

### Post by AlBundy on 2005-06-03
[QUOTE=CrustyDOD]Hey

i installed VHCS, ran: sudo /var/www/vhcs2/engine/setup/vhcs2-setup

entered data and after email i get this:

 

so did i enter password wrong? NO!
tried: mysql -u root -p and entered the same password and i can log in to mysql just fine..

So what's wrong with it??

PS: i tried about 8 times so i'm sure i entered the correct password!

Edit: should there be my password on setup screen: Please enter system SQL password (Enter for defaults) [none]:

also tried with empty and also doesn't work..

If i go to gui page i get this error, which is strange: Warning: mysql_connect(): Access denied for user: 'root@localhost' (Using password: NO) in /var/www/vhcs2/gui/include/adodb/drivers/adodb-mysql.inc.php on line 235

Using password: NO ?!?

Can i write mysql password manually into some config file or what, cause its clear the setup isn't saving/registering it no matter what i type..[/QUOTE]

I've got the same problem. Try this:

Troublesshooting

Q.When i run /var/www/vhcs2/engine/setup/vhcs2-setup file, i get errors something about mysql error
this error has occured because your mysql password contains non alpha-numeric charachters, this can be solved by editing /var/www/vhcs2/engine/setup/vhcs2-setup, so:
Code:

sudo pico /var/www/vhcs2/engine/setup/vhcs2-setup


Ctrl + w to search, type "setup_sql" without quotes
go down and find the line
Code:

my $cmd = "$main::cfg{'CMD_MYSQL'} --user=$main::db_user --pass=$main::db_pwd < /tmp/db.sql 1>/tmp/db.sql.stdout 2>/tmp/db.sql.stderr";



replace in it
Code:

--pass=$main::db_pwd



with
Code:

--pass=\"$main::db_pwd\"



so it will look like this
Code:

my $cmd = "$main::cfg{'CMD_MYSQL'} --user=$main::db_user --pass=\"$main::db_pwd\" < /tmp/db.sql 1>/tmp/db.sql.stdout 2>/tmp/db.sql.stderr";


run /var/www/vhcs2/engine/setup/vhcs2-setup again

---

### Post by CrustyDOD on 2005-06-03
Did that thing with quotes it didn't helped! My password doesn't contain any special chars..

Solution: reinstalling fresh ubuntu server and vhcs and it worked, thank god i have my server for testing and learning purposes only :)

It's strange tho that if you already have apache, mysql,... installed and running and if you remove them, vhcs doesn't work..

Oh anyone has any clue why if i send mail to my domain name that was configured by VHCS it takes like 3 hours or so to deliver and its delivered 6 times the same email :)
But if i send email from my server over that webmail, gmail receives it like 2 seconds later.. none of the config files were changed..

Ah i have so many questions! Someday, someday.. :)

---

### Post by boosted on 2005-06-07
I have everything installed.....  and the admin, reseller and domain etc..  I just got some questions!  when someone views my site all they get is the main vhcs log on page?  I remember at one point I had the vhcs tools page come up ..not sure how i did that but now just the main log on page comes up.  So what do I need to edit or replace to have my web site come up instead?  Also if some one could walk me through installing SMH (simple machines forum) that would be great!  oh and if I change/replace the php or html file so that my site will appear and not the log on screen....  how would I get to the log on screen if I wanted to?

---

### Post by robertsim007 on 2005-06-12
Similar to what boosted said, I only seem to be able to see the log-in page of VHCS.

It works nicely, and 100%, except when a domain is accessed, it loads up the log-in page.

I am still a noob to server administration, but I am not a noob to Linux.

I hate requesting help, but as you can see, I am.

I apologize if you consider this post poor.

Robert

---

### Post by Gandalf on 2005-06-13
[QUOTE=robertsim007]Similar to what boosted said, I only seem to be able to see the log-in page of VHCS.

It works nicely, and 100%, except when a domain is accessed, it loads up the log-in page.

I am still a noob to server administration, but I am not a noob to Linux.

I hate requesting help, but as you can see, I am.

I apologize if you consider this post poor.

Robert[/QUOTE]
 look back to the TUTO on the first post, troubleshooting section everything is explained there

---

### Post by wapsters on 2005-06-14
Where do i change dns settings ?  :roll:

---

### Post by TTT_travis on 2005-06-21
Me and 2 other people tried installing VHCS on fresh install of Ubuntu, it looked as if everything had gone great, we were getting the right place place holders for domains, however when we rebooted we lost the place holders and all domains now went to the vhcs login screen instead of the place holder the only way to fix this was to run ./vhcs-uninstall and then ./vhcs-setup and resetup all accounts and domains however on reboot it did the same thing as before and we were back to the login screen. Anyone else have this problem, are all 3 of us doing something wrong?

Travis

---

### Post by Gandalf on 2005-06-22
[QUOTE=wapsters]Where do i change dns settings ?  :roll:[/QUOTE]
 domain dns are under /var/cache/bind/domain.tld.db

must also be copied to /etc/vhcs2/bind/working

---

### Post by Gandalf on 2005-06-22
[QUOTE=TTT_travis]Me and 2 other people tried installing VHCS on fresh install of Ubuntu, it looked as if everything had gone great, we were getting the right place place holders for domains, however when we rebooted we lost the place holders and all domains now went to the vhcs login screen instead of the place holder the only way to fix this was to run ./vhcs-uninstall and then ./vhcs-setup and resetup all accounts and domains however on reboot it did the same thing as before and we were back to the login screen. Anyone else have this problem, are all 3 of us doing something wrong?

Travis[/QUOTE]
 How did you setup vhcs? i mean using public IP or the IP private to your network?

---

### Post by TTT_travis on 2005-06-22
[QUOTE=Gandalf]How did you setup vhcs? i mean using public IP or the IP private to your network?[/QUOTE]

we all set our up using our internal ip mine being 192.168.1.4

---

### Post by Gandalf on 2005-06-22
[QUOTE=TTT_travis]we all set our up using our internal ip mine being 192.168.1.4[/QUOTE]
 ok and if you go to [http://www.dnsreport.com](http://www.dnsreport.com) and put your site, you'll see public or privata IPs? i suppose you're using ur server for DNS too by that question

in any case, Try the following


now proceed to edit the apache files to resolve correctly
Open /etc/vhcs2/apache/parts/{prefix}_entry.tpl where {prefix} is "als" and "dmn" and "sub" without quotes
replace
```

<VirtualHost {DMN_NAME}>

```

with
```

<VirtualHost *>

```

also you need to change the already created one (same as above) but for the files
/etc/apache2/sites-available/vhcs2.conf chen you change it copy it to /etc/vhcs2/apache/working folder

---

### Post by TTT_travis on 2005-06-22
it says my ip is public, currently I am using AFRAID.org for my DNS if I start hosting I will figure out bind. I am going to try what you said and report back.

---

### Post by Gandalf on 2005-06-22
[QUOTE=TTT_travis]it says my ip is public, currently I am using AFRAID.org for my DNS if I start hosting I will figure out bind. I am going to try what you said and report back.[/QUOTE]
 ok if you don't host dns, reporting dnsreport.com results is useless

the above solution may solve the problem

good luck

---

### Post by TTT_travis on 2005-06-22
it worked! Thanks for the awesome script!

---

### Post by Gandalf on 2005-06-22
[QUOTE=TTT_travis]it worked! Thanks for the awesome script![/QUOTE]
 You're welcome ;)

---

### Post by theonewhoismany on 2005-06-26
awesome script. it worked prefectly!

i'm now trying to install GD and i need to know where it installed php and for the life of me can't find it.

any chance you know what dir it installed php too?

---

### Post by Gandalf on 2005-06-26
[QUOTE=theonewhoismany]awesome script. it worked prefectly!

i'm now trying to install GD and i need to know where it installed php and for the life of me can't find it.

any chance you know what dir it installed php too?[/QUOTE]
 PHP is installed via deb package
so it is under
/usr/bin/
/var/lib/php4/
/etc/php4/
/usr/share/php/

---

### Post by jimakira on 2005-07-04
hi 
first of all 10x for the nice guide. Exelent work :)

i have a question the email system on my setup is runnig fine, i can send and recive email via webmail also create accounts without problem, but i cant setup pop3 client like thunderbird to work with the server ... it always says login failed.

any ideas .. at least where to start looking for errors

---

### Post by steffen on 2005-07-05
[QUOTE=jimakira]hi 
first of all 10x for the nice guide. Exelent work :)

i have a question the email system on my setup is runnig fine, i can send and recive email via webmail also create accounts without problem, but i cant setup pop3 client like thunderbird to work with the server ... it always says login failed.

any ideas .. at least where to start looking for errors[/QUOTE]

Is port 110 open for POP3?

---

### Post by jimakira on 2005-07-05
here is netstat
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     11747/named
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     3689/proftpd: (acce
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     11808/master
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     11747/named
tcp6       0      0 :::110                  :::*                    LISTEN     7068/couriertcpd
tcp6       0      0 :::143                  :::*                    LISTEN     7052/couriertcpd
tcp6       0      0 :::80                   :::*                    LISTEN     26878/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     3607/sshd
tcp6       0      0 :::25                   :::*                    LISTEN     11808/master
tcp6       0      0 ::1:953                 :::*                    LISTEN     11747/named

here is telnet to it ... i dont know howto test it forsure
root@ubuntu:~# telnet localhost pop3
Trying 127.0.0.1...
Connected to ubuntu.local.
Escape character is '^]'.
+OK Hello there.
EHLO host.com
-ERR Invalid command.
USER jimakiar
+OK Password required.

dunno howto send pass manualy but pop3 client ... thunerbird in my case says Failed to login. So ... i dont know what to do next

---

### Post by cpellizzi on 2005-07-11
Gandalf-

I had some strange things happen to my server upon using this script... I would appreciate an explaination on why these things were happening...

1) For some reason, init.d was completely disabled, and I had no clue how my services were being started, whereby I could not start anything else on boot.

2) All of the original configuration files for servers such as postfix were moved to the vhcs directory. Basically, everything was moved to strange places.

3) some standard functions in postfix were not working (they usually work for me), such as the helo function

Thanks.

---

### Post by jpincheira on 2005-07-25
guys. I did not have any problem installing vhcs, but I have a problem with internet dynamic ip address: I have dynamic ip address, so can I use vhcs with zoneedit dns? Thanks. The soft is really clean and cool.
Thanks for reply! :-)

---

### Post by majikstreet on 2005-07-29
When I go to [http://myip/vhcs2/](http://myip/vhcs2/) I get a blank page, not a "Page can not be found" error, just blank page :(

I have *not* had good luck with linux so far.....

majikstreet

---

### Post by majikstreet on 2005-08-01
[QUOTE=majikstreet]When I go to [http://myip/vhcs2/](http://myip/vhcs2/) I get a blank page, not a "Page can not be found" error, just blank page :(

I have *not* had good luck with linux so far.....

majikstreet[/QUOTE]
 It myseriously works now.
Hmph, I just edited this post and I saw the control panel at my ip!! 

Nevermind!

Thanks so much!

Majikstreet

---

### Post by Finchwizard on 2005-08-18
2.4.6 is out.

Going to update that Gandalf?

Also can you run your script over the top of an existing install of VHCS and it upgrade?

Cheers
Finchwizard

---

### Post by Emnitec on 2005-08-23
I Found the answers myself and have everything up'n running now, and MAN what a beutyful app and script this was!!! Been struggling for years now to get a proper server working in Linux and UBUNTU/VHCS + the script made it in minutes!!

/Emnitec

 

****************************************************************
Hello!

My english isn't so very good, so I'm sorry if the answer for my question is already given..but...

Could someone here explain for a noob how to install VHCS on a system with dynamic IP and no-ip client to handle the domains. Everything works fine with only one domain added in VHCS but when I try to add more, Apache complains about:

"Apache2: Could not determine the server's fully qualified domain dame, using 192.168.0.128 for ServerName"

"[warn] NameVirtualHost 192.168.0.128:0 has no VirutalHosts"

"[warn] VirtualHost *domain*.com:0 overlaps with VirtualHost *domain*.se:0, the first has precedence, perhaps you need a NameVirtualHost directive"


Thans in advance!

/Emnitec, Sweden

---

### Post by warptrosse on 2005-09-03
Hi, good work Gandalf...
anyone, I have a following problem:

```
sudo /etc/init.d/proftpd restart
sudo: unable to lookup sofia via gethostbyname()
Restarting ProFTPD ftp daemon..
.. - getaddrinfo 'sofia' error: Name or service not known
 - warning: unable to determine IP address of 'sofia'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd.conf'
.
 done.
```

how i can fix it????

thanks...

---

### Post by HarabanaR on 2005-09-03
Hi everyone

Now I have installed VHCS and created a reseller, a template, a domain and there i have created some emails, databases and so on. That has all worked. 

But after I create a FTP user and try to connect to the machine locally i'm unable to connect. The message I get is:

```
Connected to svp_is.local.
421 Service not available, remote server has closed connection
``` 

Am I doing sth wrong or is it just not possible to connect locally. (I have another ubuntu box, not running VHCS, but runnig FTP service and I can connect locally to that box. 

Plz help me with this.. this box will really start hosting some sites :D

---

### Post by farao on 2005-09-13
Hi Gandalf,

I really *LOVE* your script, it did the trick in one go (well, that was after a struggle with Debian, once I took the Hoary-installer to hand, it was up and running within 1.5 hours).
What I dearly miss though, are spamassassin and clamav. I'd like to provide anti-spam and anti-virus as well, but I'm rather new to Linux, and would like some pointers. I don't have an extensive userbase, but there is quite a lot of spam rolling into my server at the moment.
It would be nice to give users the possibility to enable anti-spam and use a different mailbox for it, and the same goes for anti-virus (and if not, force it on them, since that saves my bandwidth).

I know you're not the vhcs programmer, but since all the other apps are installed by your script, I thought I'd ask.

Best, Farao

---

### Post by ejms07 on 2005-09-14
Which is the best webmail (with Calendar and Contacts) program for VHCS?

Right now I'm using phpGroupWare with it but I have to create the email accounts twice.  I want to avoid that and just create the email accounts on VHCS only.

Thanks for any help!......Ubuntu Rocks!

---

### Post by pitu on 2005-09-28
hello, concerning the domain names that dont show up, but the vhcs log in screen... i have found the following link :

how to generate ip based virtual hosts:
[http://vhcs.net/new/modules/phpwiki/index.php/HowTo%20Generate%20IP%20based%20Virtual%20Hosts%20%28en%29?version=1](http://vhcs.net/new/modules/phpwiki/index.php/HowTo%20Generate%20IP%20based%20Virtual%20Hosts%20%28en%29?version=1) 

 but i can not get the process done...cause it is not well explained at the end
where it says something had to be done with the httpd.conf file...

 if someone gets this...it may be helpfull to share it :)

 plus

---

### Post by theonewhoismany on 2005-09-30
[QUOTE=pitu]hello, concerning the domain names that dont show up, but the vhcs log in screen... i have found the following link :
how to generate ip based virtual hosts:
[http://vhcs.net/new/modules/phpwiki/index.php/HowTo%20Generate%20IP%20based%20Virtual%20Hosts%20%28en%29?version=1](http://vhcs.net/new/modules/phpwiki/index.php/HowTo%20Generate%20IP%20based%20Virtual%20Hosts%20%28en%29?version=1) 
but i can not get the process done...cause it is not well explained at the end
where it says something had to be done with the httpd.conf file...
if someone gets this...it may be helpfull to share it :)
plus[/QUOTE]

i'm having exactly the same problem!

does anyone know how to fix it the above guide doesn't fix it.

---

### Post by huwbie on 2005-10-24
Does any body know if this is going to work on Breezy??

---

### Post by steffen on 2005-11-08
[QUOTE=huwbie]Does any body know if this is going to work on Breezy??[/QUOTE]

I'm not sure how far I'm able to pull this. But I actually had a Debian Sarge server, with VHCS2 installed through apt-get from repository > deb [http://apt.scunc.org/](http://apt.scunc.org/) sarge mainIt was working fine.

Today I simply changed the sources in /etc/apt/sources.list to the Ubuntu Breezy sources, and did a dist-upgrade. Things seem to be working good so far. The only thing that changed was php.ini which is now reporting all errors to the screen. I'm surprised that this was such an easy upgrade, considering the change to GCC4, etc. I was expecting alot more trouble.

One thing I noticed however, is that I'm still on kernel 2.4.27-2-686. Don't know why that is, considering I did a dist-upgrade with the Ubuntu sources.

I'll post any problems to this thread, if/when I discover any. This will be my new production server, so I am a bit anxious, but I'd really like to run Ubuntu instead of Debian, and I think it's really nice to use repositories. I'll keep with this for a few weeks, and if it works, I'll transfer my stuff to this server. If anyone has any major warnings about doing this, please let me know :)

---

### Post by steffen on 2005-11-10
Only issue I have so far, is that VHCS doesn't configure the DNS (bind9) for me. It seems as if the VHCS installation only supports one nameserver on one server. However, most domain names requires at least two nameservers in the zonefile.

How do most people resolve this issue? As far as I'm concerned this is a crucial feature of any virtual hosting control panel, and there must be some way of easily rectifying this for all the people using VHCS.

Any suggestions on how you have solved this is appreciated!

---

### Post by gg234 on 2005-12-02
check this link for good installation article [www.debianhelp.co.uk/vhcs.htm](www.debianhelp.co.uk/vhcs.htm)






[QUOTE=steffen]Only issue I have so far, is that VHCS doesn't configure the DNS (bind9) for me. It seems as if the VHCS installation only supports one nameserver on one server. However, most domain names requires at least two nameservers in the zonefile.

How do most people resolve this issue? As far as I'm concerned this is a crucial feature of any virtual hosting control panel, and there must be some way of easily rectifying this for all the people using VHCS.

Any suggestions on how you have solved this is appreciated![/QUOTE]

---

### Post by steffen on 2005-12-03
That link doesn't say anything about setting up two nameservers, does it?

---

### Post by Shibumi on 2005-12-16
Installation went great and I have created a reseller and a user account to go with it.  Problem is, whenever I surf to the domain the /usr/www/ files show up rather than the virtual site, giving access to all the installed files for VHCS.

This happens if I simply go to the initial startup page of [http://localhost/vhcs2](http://localhost/vhcs2) as well

Any way to overcome this?


Never Mind. I found my mistake.  I skipped a step to append to the httpd.conf file {Include /etc/apache2/sites-available/vhcs2.conf}
Once I did this, all my sites started with the VHCS login screen.

---

### Post by Zelut on 2006-02-01
I'm having an issue regarding updating users.  I edited a user today to increase the number of Dbs allowed on the account.  Now the user appears to be in permanent 'waiting to be updated' stage.  Any ideas on this?  During this time I am unable to login as this user.

---

### Post by Gandalf on 2006-02-02
Vhcs daemon wasnt running apparently, try running /var/www/vhcs2/engine/vhcs2-rqst-mngr
if that worked, then run
update-rc.d vhcs2_daemon defaults

---

### Post by sebastjanp on 2006-03-19
Hello Gandalf and thanks for the beautifull scrip you wrote.

I think everythink in workin only when I click on Webmail link it gives me the error bellow.

```
ERROR (2): Header may not contain more than a single header, new line detected. (vhcs2/gui/tools/webmail/inc/inc.php:155)
```

What is the problem?

---

### Post by Zelut on 2006-03-19
I ran into that same problem recently.  I did a search for that error on the vhcs.net forums & found a fix for it.

give that a try.  If you dont find it I'll look into what I did & share.

---

### Post by sebastjanp on 2006-03-19
[QUOTE=sebastjanp]Hello Gandalf and thanks for the beautifull scrip you wrote.

I think everythink in workin only when I click on Webmail link it gives me the error bellow.

```
ERROR (2): Header may not contain more than a single header, new line detected. (vhcs2/gui/tools/webmail/inc/inc.php:155)
```

What is the problem?[/QUOTE]
I have found it. TNX kujaedz :)

this solves the problem:
```
Change /var/www/vhcs2/gui/tools/webmail/inc/inc.php line 155 from

Header("Expires: Wed, 11 Nov 1998 11:11:11 GMT\r\n".
"Cache-Control: no-cache\r\n".
"Cache-Control: must-revalidate");

to

Header("Expires: Wed, 11 Nov 1998 11:11:11 GMT");
Header("Cache-Control: no-cache");
Header("Cache-Control: must-revalidate");
```

Because a header cannot contain new lines.

EDIT:
I have left the "\r\n" inside and it still works.

---

### Post by rawoo on 2006-03-22
Hi, as a newbie I'm attempting to setup VHCS on a fresh installation of Ubuntu 5.10 using this HOWTO, but am having some problems. It appears the automatic script at "wget http://www.siemens-mobiles.org/vhcs/vhcs.sh" is not available. Is there another source for this script.

Also, when trying the manual method of this installation, typing in the very first command "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse" on step 0, I get a message that bash doesn't have a deb command. Is there such a command? What am I doing wrong? Any help would be appreciated.

---

### Post by sebastjanp on 2006-03-22
[QUOTE=rawoo]
Also, when trying the manual method of this installation, typing in the very first command "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse" on step 0, I get a message that bash doesn't have a deb command. Is there such a command? What am I doing wrong? Any help would be appreciated.[/QUOTE]

This is an new line which should be added at the end of the sources.list file and not started as an command inside terminal.

```
sudo vi /etc/apt/sources.list
```

To start editing the file press insert button on your keyboard and uncomment that line (delete # sign at the start) and then press Esc button to exit edit mode and than enter : sign to tell vi that you want to start a command, and then wq which stands for write & quit.

If you are instaling inside xserver you could use gedit instead vi. Its more graphical an easy to use for a fresh ubuntuers.

```
sudo gedit /etc/apt/sources.list
```

I hope that helps :D

Oh ya, about new location of the script. I think that I had the same problem but I have tried second time and the script was downloaded from a new location but I don't remember from where. Sry

---

### Post by rawoo on 2006-03-23
Thanks for the help. How silly of me. :-D  I'll add the first few lines to the sources.list and give it a go.

BTW, I tried the link to the auto script...still can't get to the website. Anyone have the script they could email to me?

---

### Post by sebastjanp on 2006-03-23
I have atached it on this post. I hope Gandalf doesn't mind.

And if you mind please contact me and I will delete it immediatly.

---

### Post by Gandalf on 2006-03-23
[QUOTE=sebastjanp]I have atached it on this post. I hope Gandalf doesn't mind.

And if you mind please contact me and I will delete it immediatly.[/QUOTE]
No i don't mind posting it, but since my server is down due to HDD failure, the script is useless without the files...

I will later post another source to get it, untill I get my server ready again

---

### Post by sebastjanp on 2006-03-23
Well I hope you'll do it asap because I have to awake my main windows zombie server into a new ubuntu mail&file server :D. 
And I'm lost without your script :)

---

### Post by rawoo on 2006-03-24
Okay, I got vhcs install without any significant problems. Thanks all for your help, and of course for the wonderful HOWTO:-D 

The index page shows up as expected. Now another questions....where are the manuals for VHCS. vhcs.net has the online wiki in English, but the few pages there are severely lacking. Can anyone direct me to a complete howto on the use of vhcs. I can't figure out how to get onto the administrator's control panel page.

Thanks,
Richard

---

### Post by guysmiley on 2006-03-27
Hey guys,

Total noob on linux...  I tried wget wget [http://wael.nasreddine.com/files/vhcs/vhcs.sh](http://wael.nasreddine.com/files/vhcs/vhcs.sh) and failed.  Where are you guys acquiring your version of vhcs from?

---

### Post by guysmiley on 2006-03-28
Bump

---

### Post by rawoo on 2006-03-28
[QUOTE=guysmiley]Hey guys,

Total noob on linux...  I tried wget wget [http://wael.nasreddine.com/files/vhcs/vhcs.sh](http://wael.nasreddine.com/files/vhcs/vhcs.sh) and failed.  Where are you guys acquiring your version of vhcs from?[/QUOTE]



Hi,
Got my script from [http://sol.cs.uwindsor.ca/~anas/vhcs/vhcs](http://sol.cs.uwindsor.ca/~anas/vhcs/vhcs). It's setup for Breezy.

---

### Post by spanishwasabi on 2006-04-06
Hi,

After an apparently good installation, going to  [http://192.168.1.2/vhcs2/](http://192.168.1.2/vhcs2/) gives me the following error message:
"""
Can not open the vhcs2.conf config file !

Pleas contact your system administrator
"""

I'm the system administrator, so I'm in trouble :-P

I checked all the vhcs2.conf files of my system, and they're all in rw-r--r-- mode, so I don't understand why the system can not see them.

I'll also greped for safe_mode in my files and it's always Off.

Can someone suggest a solution or a place where more information can be found?

Thanks

G

---

### Post by heislord5 on 2006-04-12
Hi,

I setup server with no problems...lol...was easier than setting up my wireless card!  I get the default page for my website.  I use zoneedit.  Server has internal ip from router.  Apparently all that is working fine.  I have ddclient or whatever it is called to update the ip address.  No problem getting to my website [www.predestine.org](www.predestine.org).

Can get to webmail after fixing the before mentioned Header on multiple lines problem.

Can send myself mail in mock account:   [email]random@predestine.org[/email].
I receive it from my own account.
Do not receive email from other accounts.  Emails sent to other accounts do not arrive.

dnsreport says:
> 
Getting MX record for predestine.org (from local DNS server, may be cached)... Got it!

Host	Preference	IP(s) [Country]
mail.predestine.org.	0	[No IP found]

help please?  I really appreciate it.

---

### Post by heislord5 on 2006-04-12
Removed MX record & added A record for mail.predestine.org at zoneedit.com

---

### Post by heislord5 on 2006-04-12
Added MX record back in at zoneedit help's request...it seems to find everything now at dnsreport.com.  Don't know why it didn't before...but oh well.  So now have both A and MX record for mail.predestine.org

---

### Post by heislord5 on 2006-04-16
mailserver just stopped sending mail.  It worked for a while and just stopped.  It still receives mail.  I can't get it to send from Evolution or from webmail (although in both it says it was sent....just never arrives on the other side).

Since it doesn't work from webmail, I have to assume it is either the server or the DNS entry that is wrong.  Using zoneedit for DNS server.

I need to know what is the correct set of entries for DNS...I've been told I need both A records and a MX record.

I've tried several variations but it's hard to tell which one you're using at a particular point in time since it takes a little while for a change to take effect.

Right now A-record entries:
[www.mydomain.org](www.mydomain.org)    11.11.11.11 
mydomain.org            11.11.11.11
ftp.mydomain.org       11.11.11.11
mail.mydomain.org     11.11.11.11
I added the following because of the problems I'm having:
smtp.mydomain.org   11.11.11.11
pop3.mydomain.org    11.11.11.11

MX record:
mail.mydomain.org {handles mail for} mydomain.org
I added the following because of the problems:
{Secondary}  smtp.mydomain.org {handles mail for} mydomain.org
{terniary} pop3.mydomain.org {handles mail for} mydomain.org

(my real ip is there, found at whatsmyip.org...also the website shows up and incoming mail gets here, so I am using the correct ip).  The entries I added I don't believe should be there, but I'm just trying whatever I can.  In the admin console, it says both pop3 and smtp servers are up.  Doesn't list a mail server other than those two.

What are the right settings for A records and MX records?

Thanks,

heislord5

any ideas?  Gandalf?

---

### Post by golfreeze on 2006-04-22
Today i have some problem about install VHCS in ubuntu 5.1 with AMD 64 bit.
where i can download the script with 64 bit?
and if anyone know about some mirror that for 64 bit please tell me coz i must finish this work in a few days

Thank you very much
       Golf :-|

---

### Post by Gandalf on 2006-04-23
Hi,

I'm sorry but there's no 64 version, simply because i don't own an 64 machine so i can't test nor program fro it, though am surprised it didn't work, u should only get the packages names designed for 64 version

P.S: for all who have VHCS Be sure you have the latest VHCS patches installed, I got freaking hacked as well as many ppl, so be carefull, restrict /vhcs2/ within .htaccess if u can...

---

### Post by guysmiley on 2006-04-27
Gandalf,

Thanks for the heads up on patches/hacking...  Do you know how hackers can tell if you have vhcs?  Do they have some kind of bot they use to roam the web searching for instances of vhcs?

gs

---

### Post by Gandalf on 2006-04-30
Yes they are using a bot called Google :P
[http://www.google.com/search?hl=en&q=VHCS%C2%AE+Pro+v2.4+build%3A+Spartacus&btnG=Google+Search](http://www.google.com/search?hl=en&q=VHCS%C2%AE+Pro+v2.4+build%3A+Spartacus&btnG=Google+Search)
That's a copy of the url i Find out with the Apache log, and I also have the site from where the hacker are coming, but sorry this won't be published in public, a tip, the site is for some security guy who was working on discovering the holes of VHCS and unfortunately he Gave a lot of information on how to do it, actually he made a simple page which the hacker put the URL of the VHCS2 site and he get access without any real work!!!

---

### Post by Trocisp on 2006-05-04
When I get here.
```
sudo apt-get install -y ssh postfix postfix-tls proftpd-mysql courier-authdaemon courier-base courier-imap courier-maildrop courier-pop libberkeleydb-perl libcrypt-blowfish-perl libcrypt-cbc-perl libcrypt-passwdmd5-perl libdate-calc-perl libdate-manip-perl libmime-base64-perl libdbd-mysql-perl libdbi-perl libio-stringy-perl libmail-sendmail-perl libmailtools-perl libmd5-perl libmime-perl libnet-dns-perl libnet-netmask-perl libnet-perl libnet-smtp-server-perl libperl5.8 libsnmp-session-perl libterm-readkey-perl libtimedate-perl perl perl-base perl-modules bind9 diff gzip iptables libmcrypt4 mysql-client mysql-common mysql-server patch php4 php4-mcrypt php4-mysql php4-pear procmail tar original-awk libterm-readpassword-perl libsasl2-modules libsasl2 sasl2-bin apache2 apache2-common apache2-mpm-prefork libapache2-mod-php4 bzip2
```

I get this error message

```
Reading package lists... Done
Building dependency tree... Done
Package libmime-base64-perl is a virtual package provided by:
  perl 5.8.7-5ubuntu1.2
You should explicitly select one to install.
E: Package libmime-base64-perl has no installation candidate

```

---

### Post by da_shrewd on 2006-06-06
I'm using Ubuntu dapper version. The script doesn't work with dapper. How i can solve my problem? Anybody can help me?

Thanks,
Syahir-Malaysian.

---

### Post by mikeeblau on 2006-06-10
Hi da_shrewd,

I think that this will help you: :D 
[http://www.thermalogic.de/vhcs-on-ubuntu-server.html]("http://www.thermalogic.de/vhcs-on-ubuntu-server.html")

Best regards,
mikeeblau

Special thx to Gandalf!

---

### Post by Gandalf on 2006-06-10
Hi mikeeblau

I think u have some bash knowledge and I'm looking for someone to help in a complete rewrite of the script to use dialog (which is already done, i still have some hacks to re-write), are you interrested??

---

### Post by Gandalf on 2006-06-10
Script updated to install VHCS on Dapper, can someone test it please ??

---

### Post by da_shrewd on 2006-06-12
gandalf, i want to try:D

---

### Post by Gandalf on 2006-06-12
[QUOTE=da_shrewd]gandalf, i want to try:D[/QUOTE]
Hi,

Okay send me an [email](http://wael.nasreddine.com/component/contact/Administrator/Wael_Nasreddine/) and i'll create an svn account for you to work on it, I worked on it yesterday and it's getting better

OH btw just for curious.
svn co svn://wael.nasreddine.com/wael/trunk/projects/easyvhcs
login : vhcs
password : vhcs
(anonymous svn account)

Regards,
Wael Nasreddine

---

### Post by mikeeblau on 2006-06-13
Hi Gandalf,

sry for late response, but I had a little excursion to IPConfig. Now I am back and I feel confident with VHCS as ever before. :D

Regarding the error, reported from Duroniux on 2006-06-12 12:48:37:
> Package postfix-tls is a virtual package provided by: 
postfix 2.2.4-1ubuntu2.1 
You should explicitly select one to install. 
E: Package postfix-tls has no installation candidate 
ERROR # 100 : There was an error installing required packages. 


I got the same error too and removed that postfix-tls entry, as you can see in my adapted script at [http://www.thermalogic.de/vhcs-on-ubuntu-server.html]("http://www.thermalogic.de/vhcs-on-ubuntu-server.html"). All works fine now. As the comment tell us, it's a virtual package and you have to decide to take that one or postfix only and not both. ;) 

Coming back to your offer to assist you: thank you for that offer but at present I am full of work. I hope that there are others who may help you.

Keep going on with that good work! =D> \\:D/ 

Regards,
mikeeblau

---

### Post by wr19026 on 2006-06-15
First of all, great job on the HOWTO and script! I have looked at ISPConfig as well but had (more) problems getting it to work than VHCS :) Where VHCS really seems to be lagging is in the documentation btw....

Anyway, I have successfully installed VHCS but now I'm runnig into a problem. 

Here's what I've set up on a brand new Ubuntu 6.06 LTS Server installation:

Host: server
Domainname: lastname.net
hostname and hostname -f shows server.lastname.net

I ran Gandalf's install script to install the latest version of VHCS, which it did without any problems. So far, so good.

Then I log in to VHCS [http://10.0.0.1/vhcs2](http://10.0.0.1/vhcs2) (as admin). Again, this works.

So what I really want to do is make sure that lastname.net is active (again) and that I can send and receive e-mail.

So I set up a reseller: lastname, and log back in as him. Again, no problems. Great GUI by the way!

Now as the reseller I create a customer. Since the customername is the domainname (VERY convenient) the customer created is lastname.net. So I log in as lastname.net and add 2 e-mailusers: myself(@lastname.net) and postmaster(@lastname.net).

I can log in as either user using webmail. Still, no problem at all. I also see the mail directories in /var/mail/virtual/lastname.net. 

I then made the following changes to /etc/postfix/main.cf as suggested on the VHCS Forum @ vhcs.net:
postconf -e 'mydomain = lastname.net'
postconf -e 'myhostname = server.lastname.net'
postconf -e 'relayhost = [mailrelay.direct-adsl.nl]'
postconf -e 'smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination'
postconf -e 'smtpd_sasl_local_domain ='

Obviously I restarted Postfix after applying these changes.

Now I try to send mail: [email]myself@lastname.net[/email] sends mail to [email]myself@employer.com[/email] (a domain that I do not host so truely outside of my control). The e-mail arrives very shortly after it's been sent without any problems.

Now I send an e-mail from [email]myself@employer.com[/email] to [email]myself@lastname.net[/email] but instead of receiving it I get this error in /var/log/mail: 

Jun 15 13:07:33 server postfix/trivial-rewrite[15932]: warning: do not list domain lastname.net in BOTH mydestination and virtual_mailbox_domains
Jun 15 13:07:33 server postfix/qmgr[15864]: 0E9A82EC6A4: from=<myself@employer.com>, size=1655, nrcpt=1 (queue active)
Jun 15 13:07:33 server postfix/qmgr[15864]: 63AEF2EC6A5: from=<myself@employer.com>, size=1688, nrcpt=1 (queue active)
Jun 15 13:07:33 server postfix/local[15933]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jun 15 13:07:33 server postfix/local[15934]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jun 15 13:07:33 server postfix/local[15933]: 8D3C02EC691: to=<myself@lastname.net>, relay=local, delay=1368, status=bounced (unknown user: "myself")

My understanding is that the first line is a warning and not a real error, so the issue must be elsewhere. I mean, this cannot mean that VHCS does not allow you to host web and e-mail for your own domain?

In other words, can anyone please help me understand what I need to change to be able to receive e-mail in my setup?

Thanks in advance!

---

### Post by serkanhamarat on 2006-06-16
I prefer php5. 
I also started to install VHCS with installed one.
But script uninstalls 5 and replaces with php4.
I guess it is not necessary.

---

### Post by serkanhamarat on 2006-06-16
I just changed script as mysql-xxxxx-4.1 package names
with mysql-xxxxx in dapper section. so it can use mysql 5.0

---

### Post by serkanhamarat on 2006-06-16
Hey it's important. webmail doesn't work because a "Header" problem.
They must patch but how can we warn them?

diff -urN /var/www/vhcs2/gui/tools/webmail/inc/inc.php.old /var/www/vhcs2/gui/tools/webmail/inc/inc.php :
[COLOR="Red"]---CUT--------------------------------------------------------------------[/COLOR]
--- /var/www/vhcs2/gui/tools/webmail/inc/inc.php.old    2006-06-17 01:53:40.000000000 +0300
+++ /var/www/vhcs2/gui/tools/webmail/inc/inc.php        2006-06-17 01:54:01.000000000 +0300
@@ -150,9 +150,9 @@
 Don't remove the fallowing lines, or you will be problems with browser's cache
 */

-Header("Expires: Wed, 11 Nov 1998 11:11:11 GMT".
-"Cache-Control: no-cache".
-"Cache-Control: must-revalidate");
+Header("Expires: Wed, 11 Nov 1998 11:11:11 GMT");
+Header("Cache-Control: no-cache");
+Header("Cache-Control: must-revalidate");

 $nocache = "
 <META HTTP-EQUIV=\"Cache-Control\" CONTENT=\"no-cache\">
[COLOR="Red"]---END--------------------------------------------------------------------[/COLOR]

---

### Post by izzyonstage on 2006-06-21
Hi Gandalf,

I am fairly new to linux, but have picked up loads so far. Great script by the way.

My only problem is that the login page comes up but when i log in the next page is just blank.

Also Just wondering... I was previously having problems with ISPConfig, have now decided to use VHCS. But I was wondering if it would be possible to have Roundcube mail instead of webmail as the web-based mail client?

Is there anyway to have a choise, or do you know if and how i could change it?
This is for Breezy if poss?

Also (once i get the hang of things a bit more) would like to maybe help out if I can.

Izzyonstage

---

### Post by serkanhamarat on 2006-06-24
I guess you can create a subdomain
webmail.izzyhosting.com  for example.
then put your configured roundcube files there via ftp.

you can't add mail.izzyhosting.com as subdomain.
because of already have an MX record in DNS.
but you can add as <virtualhost> to apache2.conf

---

### Post by serkanhamarat on 2006-06-24
I have more radical solution for you. backup and clean under
/var/www/vhcs2/gui/tools/webmail/

then put the RC there \\:D/

---

### Post by Gandalf on 2006-06-24
NO don't remove the webmail it will be erased on each upgrade, BAD BAD idea..

the best solution is to do something like this, download and extract the client anywhere in the server, then create an apache file for it, for example /etc/apache2/sites-available/roundcube.conf with the following contents
```

Alias /webmail /path/to/roundcube
<Directory /path/to/roundcube>
    php_admin_value open_basedir "/path/to/roundcube"
    AllowOverride All
    Options MultiViews IncludesNoExec FollowSymLinks
</Directory>

```

then link it to sites-enabled
```

ln -sf /etc/apache2/sites-available/roundcube.conf /etc/apache2/sites-enabled/roundcube.conf

```

and reload apache
```

/etc/init.d/apache2 reload

```

Good Luck ;)

---

### Post by izzyonstage on 2006-06-27
Thanks guys, i think it will work, have got login screen up.

Now i get my vhcs login page, but when i log in with the username and password i set during the setup, all i get is a blank page, so am unable to use vhcs to setup any email aliases.

---

### Post by serkanhamarat on 2006-06-27
your's better. i screwed up in my server. but i recovered easily. i'm gonna like this vhcs. easy to manage, fun to struggle with.

---

### Post by serkanhamarat on 2006-06-27
[QUOTE=izzyonstage]Thanks guys, i think it will work, have got login screen up.

Now i get my vhcs login page, but when i log in with the username and password i set during the setup, all i get is a blank page, so am unable to use vhcs to setup any email aliases.[/QUOTE]

i assume that you don't think it's related with roundcube.

so many things causes blank-pages in php projects like this. 
try to "view source" of that blank page. maybe gives an idea.
or you can set php 'debug level' to 'high' to view something.


------------------------

:KS NEWS:
I saw this:
[http://vhcs.net/new/modules/newbb/viewtopic.php?topic_id=5799&forum=17](http://vhcs.net/new/modules/newbb/viewtopic.php?topic_id=5799&forum=17)
Have a look at.

---------------------

---

### Post by serkanhamarat on 2006-06-27
hi,
i used my new server in last 6 days.

funny think is, i found a thousand courier authdaemon process spawned. it was five when i was install the server. (as written in relevant line in courier confs: "daemons=5")

and number still increases. 

any idea?  :-k 


PS: i stopped courier-pop, courier-imap, courier-authdaemon then
i killed the rest with killall. (/etc/init.d/courier-* stop   not stopped all)
then start again. authdaemon starts with 5, it's okay.
but later, spawn excesses again.
i can't find anything in exngine/  or /etc/vhcs2/

---

### Post by XplOzIOn on 2006-07-17
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ERROR # 100 : There was an error installing required packages.

Help.
dont know what it might be...

---

### Post by serkanhamarat on 2006-07-25
> **XplOzIOn said:**
> Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ERROR # 100 : There was an error installing required packages.

Help.
dont know what it might be...


Your problem might be in /etc/apt/sources.list

"man sources.list" then google "ububtu sources.list"

---

### Post by Silver Bullet on 2006-07-27
> **wr19026 said:**
> First of all, great job on the HOWTO and script! I have looked at ISPConfig as well but had (more) problems getting it to work than VHCS :) Where VHCS really seems to be lagging is in the documentation btw....

Anyway, I have successfully installed VHCS but now I'm runnig into a problem. 

Here's what I've set up on a brand new Ubuntu 6.06 LTS Server installation:

Host: server
Domainname: lastname.net
hostname and hostname -f shows server.lastname.net

I ran Gandalf's install script to install the latest version of VHCS, which it did without any problems. So far, so good.

Then I log in to VHCS [http://10.0.0.1/vhcs2](http://10.0.0.1/vhcs2) (as admin). Again, this works.

So what I really want to do is make sure that lastname.net is active (again) and that I can send and receive e-mail.

So I set up a reseller: lastname, and log back in as him. Again, no problems. Great GUI by the way!

Now as the reseller I create a customer. Since the customername is the domainname (VERY convenient) the customer created is lastname.net. So I log in as lastname.net and add 2 e-mailusers: myself(@lastname.net) and postmaster(@lastname.net).

I can log in as either user using webmail. Still, no problem at all. I also see the mail directories in /var/mail/virtual/lastname.net. 

I then made the following changes to /etc/postfix/main.cf as suggested on the VHCS Forum @ vhcs.net:
postconf -e 'mydomain = lastname.net'
postconf -e 'myhostname = server.lastname.net'
postconf -e 'relayhost = [mailrelay.direct-adsl.nl]'
postconf -e 'smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination'
postconf -e 'smtpd_sasl_local_domain ='

Obviously I restarted Postfix after applying these changes.

Now I try to send mail: [email]myself@lastname.net[/email] sends mail to [email]myself@employer.com[/email] (a domain that I do not host so truely outside of my control). The e-mail arrives very shortly after it's been sent without any problems.

Now I send an e-mail from [email]myself@employer.com[/email] to [email]myself@lastname.net[/email] but instead of receiving it I get this error in /var/log/mail: 

Jun 15 13:07:33 server postfix/trivial-rewrite[15932]: warning: do not list domain lastname.net in BOTH mydestination and virtual_mailbox_domains
Jun 15 13:07:33 server postfix/qmgr[15864]: 0E9A82EC6A4: from=<myself@employer.com>, size=1655, nrcpt=1 (queue active)
Jun 15 13:07:33 server postfix/qmgr[15864]: 63AEF2EC6A5: from=<myself@employer.com>, size=1688, nrcpt=1 (queue active)
Jun 15 13:07:33 server postfix/local[15933]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jun 15 13:07:33 server postfix/local[15934]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jun 15 13:07:33 server postfix/local[15933]: 8D3C02EC691: to=<myself@lastname.net>, relay=local, delay=1368, status=bounced (unknown user: "myself")

My understanding is that the first line is a warning and not a real error, so the issue must be elsewhere. I mean, this cannot mean that VHCS does not allow you to host web and e-mail for your own domain?

In other words, can anyone please help me understand what I need to change to be able to receive e-mail in my setup?

Thanks in advance!


Did you resolve this and if so then how. I am having the same exact issue. Cannot receive from external adresses. Sending is OK.

My main.cf is setup like yours as well.

---

### Post by serkanhamarat on 2006-07-27
> **Silver Bullet said:**
> Did you resolve this and if so then how. I am having the same exact issue. Cannot receive from external adresses. Sending is OK.

My main.cf is setup like yours as well.

If FQDN comes first, resolve issues works better.
Try this. Replace if FQDN comes later, in /etc/hosts

OLD:
==============================================
127.0.0.1     mail.local       localhost
184.116.24.3  mail  mail.prettydomain.com
==============================================

NEW:
==============================================
127.0.0.1     mail.local       localhost
184.116.24.3  mail.prettydomain.com  mail
==============================================

---

### Post by Silver Bullet on 2006-07-27
> **Silver Bullet said:**
> Did you resolve this and if so then how. I am having the same exact issue. Cannot receive from external adresses. Sending is OK.

My main.cf is setup like yours as well.

Nevermind.....got it.

I decided to heed the warning "warning: do not list domain *domain_name*.net in BOTH mydestination and virtual_mailbox_domains" and removed my domain name from main.cf and replaced it with *servername*.local, restarted postfix and voila. Everything is great now.

---

### Post by wuhaa on 2006-07-30
Hi,

I'm getting an error when installing the packages in step 5:

Reading package lists... Done
Building dependency tree... Done
ssh is already the newest version.
Package postfix-tls is a virtual package provided by:
  postfix 2.2.10-1ubuntu0.1
You should explicitly select one to install.
E: Package postfix-tls has no installation candidate

How can i resolve this issue?

Thanks.

---

### Post by joshchernoff on 2006-07-30
ok I got it installed and every thing works ok but the email has some problems. I dont know any thing about dns, thought I have made a MX record but when I try to use the webmain from the main page i get

```
ERROR (2): Header may not contain more than a single header, new line detected. (/var/www/vhcs2/gui/tools/webmail/inc/inc.php:155)
```

any ideas?

---

### Post by joshchernoff on 2006-07-30
> **wuhaa said:**
> Hi,

I'm getting an error when installing the packages in step 5:

Reading package lists... Done
Building dependency tree... Done
ssh is already the newest version.
Package postfix-tls is a virtual package provided by:
  postfix 2.2.10-1ubuntu0.1
You should explicitly select one to install.
E: Package postfix-tls has no installation candidate

How can i resolve this issue?

Thanks.

I got that too what was it?

---

### Post by serkanhamarat on 2006-07-31
> **wuhaa said:**
> Hi,

I'm getting an error when installing the packages in step 5:

Reading package lists... Done
Building dependency tree... Done
ssh is already the newest version.
Package postfix-tls is a virtual package provided by:
  postfix 2.2.10-1ubuntu0.1
You should explicitly select one to install.
E: Package postfix-tls has no installation candidate

How can i resolve this issue?

Thanks.


It's about updated ubuntu packages, not vhcs.
You should be sure about aptitude updates.
Check your /etc/apt/sources.list then up to date your linux.
If you get nothing, tell us.

---

### Post by serkanhamarat on 2006-07-31
> **joshchernoff said:**
> ok I got it installed and every thing works ok but the email has some problems. I dont know any thing about dns, thought I have made a MX record but when I try to use the webmain from the main page i get

```
ERROR (2): Header may not contain more than a single header, new line detected. (/var/www/vhcs2/gui/tools/webmail/inc/inc.php:155)
```

any ideas?


It's related with PHP guys. They changed somethings.

You should dance with codes some.
Split header messages.
Change the line 155 like this:
==================================================
Header("Expires: Wed, 11 Nov 1998 11:11:11 GMT");
Header("Cache-Control: no-cache");
Header("Cache-Control: must-revalidate");
==================================================

But beleive me, it won't be enough.
Try to use roundcube instead of this webmail.
Refer to Gandalf's messages in this thread, page 13.

---

### Post by serkanhamarat on 2006-07-31
[B]REMINDER:
Guys who uses 6.06 dapper, they should be there:
[http://ubuntuforums.org/showthread.php?t=106707]("http://ubuntuforums.org/showthread.php?t=106707")

[/B]

---

### Post by joshchernoff on 2006-08-01
yeah that was it. but now I have a problem with my smpt server or dns not sure witch. I can send and receive emails fine no problem intrenaly, but I can only receive emails from the internet not send out from my server. is there a diffrent port used to send out from the server then it is to receive? also where should I start when looking for the problem I dont know a thing about this server I'v only had it up for a few days as a learning tool. I'm a noob though I feel like a nob.

---

### Post by joshchernoff on 2006-08-01
never mind

---

### Post by serkanhamarat on 2006-08-01
if it returns an error message, it's possible to say something.

---

### Post by razor7 on 2006-08-03
> **plpeyssard said:**
> High
Thank you for this wonderfull tutorial and this FAQ which works fine and help a lot.

I use vhcs 2.4 beta version build  03-2005-21
I have some trouble about **domain statistics.** It does not work. 
Everething is 0.00 B in reseller and user screen.

I discovered that the /etc/init.d/vhcs-network daemon did not start.
here is the log message:

bind: Address already in use
ll_daemon_start: Resource temporarily unavailable

Is there a way to find that adress and change it ?
What can i do to solve that situation ?

Thanks.

Hello I have the same issue after upgrading from 5.10 to 6.06 LTS...Any Help...please...!!!


Thanks in advise.

---

### Post by ragdemai on 2006-08-03
Hi Gandalf,
Just to make sure is this will effect Virtual host in Apache2 ??
Because i having problem with Apache2 virtual host is not running,
I guest because I didn't install VHCS.

---

### Post by wuhaa on 2006-08-05
Hi,

I found that the postfix pkg has tls in it. So just remove the postfix-tls pkg from the apt-get install list.

That should work fine.

---

### Post by mitjab on 2006-09-03
Very good sript and very good howto but i have 2 questions?

i am using autoscript and i see that php4 was installed?

i sit possible to install php5. How can i upgrade it now?

And why i must select no to web directories?

Now i try [http://192.168.1.5/~mitjab](http://192.168.1.5/~mitjab) and said that not exist but i want that all users has their own public_html acount.

thx

---

### Post by volksman on 2006-09-12
damn that script works great!  Did a fresh Ubuntu 6.06LTS Workstation install and ran your script.  I now have a server.

THANKS GANDALF!!!

---

### Post by godlike on 2006-10-03
is the server down for good???????????????

---

### Post by alixky on 2006-10-09
I have follow the instruction but I guess not all the required packages installed. Thus, I got the error messages same as zybrid
 CRITICAL ERROR: Module [MIME::Entity] WAS NOT FOUND !

CRITICAL ERROR: Module [MIME::Parser] WAS NOT FOUND !

CRITICAL ERROR: Module [Crypt::CBC] WAS NOT FOUND !

CRITICAL ERROR: Module [Crypt::Blowfish] WAS NOT FOUND !

CRITICAL ERROR: Module [Term::ReadPassword] WAS NOT FOUND !

after install the additional modules: libmime-perl ( libmime-base64-perl notwork), perl-Crypt-Blowfish, perl-Crypt-CBC, libterm-readpassword-perl

I got this message:
 If specified by -literal_key, then the key length must be equal to the chosen cipher's key length of 56 bytes at /var/www/vhcs2/engine/setup/../vhcs2_common_code.pl line 1443
Compilation failed in require at /var/www/vhcs2/engine/setup/vhcs2-setup line 32.

Any idea?? btw the server stored script to run install has been down.

---

### Post by serkanhamarat on 2006-10-10
Gandalf, wael.nasreddine.com doesn't give expected old pages.
Are you aware of that :confused: 

Is there anybody have the script newer than VERSION="1.1.0c" ?

---

### Post by serkanhamarat on 2006-10-18
[COLOR="DarkRed"]WARNING[/COLOR]

Who upgrades proftpd to version 1.3.0, and gets problems with FTP login like
```

421 Service not available, remote server has closed connection

```
disable TLS/SSL modules from /etc/proftpd/modules.conf because of such old ftp clients cannot communicate.

Also you can disable radius and postgres style auth-mechanisms that unused with VHCS.

All these modules comes enabled in dapper by default.

---

### Post by Ignite_nz on 2007-04-19
Can someone help me out here, I've done exactly as the instructions say, but when I make an FTP account, I can't log in. I just see "incorrect username / password".... help!

Thanks

---

### Post by godlike on 2007-04-19
hey have u tried out the new vhcs fork yet? I thinks its called omega? just do a google for vhcs fork and u should find it. It has a newer version of vhcs worked easy for me b4 but now im not sure as i changed all my server to manual admin

---

### Post by Ignite_nz on 2007-04-19
Nice man, I'll try that out  and post back here. Cheers.

---

### Post by godlike on 2007-04-19
Anytime i remember how annoyed i got lol  


[http://isp-control.net/](http://isp-control.net/)   <----- thats the link to the project (just in case yer not a google wizard lol)

---

### Post by wuhaa on 2007-04-20
Hi,

What changes do I have to make to these instructions to install VHCS2 on Ubuntu 7.04 server???

Thanks,

---

### Post by godlike on 2007-04-21
Hrmmm not too sure i installed it on 6.10
I dont think it would be all that much diffrent though.

---

### Post by fieldsg on 2007-06-27
Went to do this and errorrs out...is site still up?

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse

---

### Post by fieldsg on 2007-06-27
> **zybrid said:**
> The solution were to install libmime-pearl 

Should it not be libmime-perl

I ran:

```
apt-get install libmime-perl
```

now I am getting:

```

CRITICAL ERROR: Module [Crypt::CBC] WAS NOT FOUND !
CRITICAL ERROR: Module [Crypt::Blowfish] WAS NOT FOUND !
CRITICAL ERROR: Module [Crypt::PasswdMD5] WAS NOT FOUND !
CRITICAL ERROR: Module [Term::ReadPassword] WAS NOT FOUND !

```


At a lose...any thoughts?

---

### Post by C.Winder on 2007-06-29
I do VHCS installations for a ONE TIME fee of $15. This also comes with Lifetime FREE support.
 If you go to the VHCS website they charge much more than this JUST for Installation. 
Then they charge even more for Support. Take this opportunity now to send me a PM or
Email me at [email]Toxic.Waste@Hotmail.Co.Uk[/email].

Don't miss out!
Regards,
Craig Winder

---

### Post by Zbrahead91 on 2007-06-29
Hi, after I download your file into usr/local/src/ and run it using sudo sh, I get this error:
[HTML]
root@EGSUKI:/usr/local/src# sh vhcs.sh
vhcs.sh: 127: Syntax error: Bad substitution
[/HTML]
I sudo'ed gnome-terminal to get root, i never login as root lol.

Sorry, just looking for the error, and it turns out feisty fawn is not supported. how do i install onto feisty fawn?

---

### Post by crafter on 2007-08-09
I got it installed on Feisty. I had two major challenges:
1. Dependencies - these are documented somehwhere on the net. There is an error in
   the Fesity cache file that must be corrected. Can't recall which one.
2. Replace /bin/sh with the bash version
    mv /bin/sh /bin/sh.bak
    mv /bin/bash /bin/sh
The install works fine then.

---

### Post by razor7 on 2007-08-09
I strongly recomend to install ISPConfig... [http://www.ispconfig.net/](http://www.ispconfig.net/)

BEst Regards.

---

### Post by circuitz on 2007-09-22
I would like to run on a fiesty server, though I can not seem to find a vhcs.sh file that will work.  Can someone provide a working link?

---

### Post by razor7 on 2007-09-22
I strongly recomend to install ISPConfig... [http://www.ispconfig.net/](http://www.ispconfig.net/)

Best Regards.

---

### Post by hagen00 on 2007-09-27
I've gotten it to work on Feisty..had to hack a bit. 

1. Get the Debian/Ubuntu install script off the website
2. Change references of Breezy to Feisty
3. Remove libnet-perl 
4. Run the script. It will install packages, but fail when trying to install VHCS
5. Get VHCS - in the Makefile i just removed any reference to SUSE, so that it assumes a Debian install
6. rm /bin/sh; ln -s /bin/bash /bin/sh
7. in vhcs2_common_code.pl to line 1444 add keysize => 32 (and wherever else in that file that same function is called)
8. Run the install script. 

In a nutshell...might be completely different for you when you try and install on feisty

---

### Post by Shaun13 on 2007-10-25
During the installation I get the error: 
```

dpkg: error processing vhcs (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of vhcs-daemon:
 vhcs-daemon depends on vhcs (= 2.4.7.1-2); however:
  Package vhcs is not configured yet.
dpkg: error processing vhcs-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vhcs-gui:
 vhcs-gui depends on vhcs (= 2.4.7.1-2); however:
  Package vhcs is not configured yet.
dpkg: error processing vhcs-gui (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vhcs
 vhcs-daemon
 vhcs-gui
E: Sub-process /usr/bin/dpkg returned an error code(1)
```

Please help?

Thanks in advance,

~Shaun

---

### Post by Shaun13 on 2007-10-26
Bump

---

### Post by drndrw on 2007-10-26
```
cd ./tools && make install
make[1]: Entering directory `/home/drndrw/Stuff/vhcs2-2.4.7.1/tools'
cd ./build && make install 
make[2]: Entering directory `/home/drndrw/Stuff/vhcs2-2.4.7.1/tools/build'
/usr/bin/install -m 0700 -o root -g root ./vhcs2-mkdirs.pl /usr/sbin
make[2]: Leaving directory `/home/drndrw/Stuff/vhcs2-2.4.7.1/tools/build'
cd ./daemon && make vhcs2_daemon
make[2]: Entering directory `/home/drndrw/Stuff/vhcs2-2.4.7.1/tools/daemon'
gcc -O2 -ansi -Wall -Wstrict-prototypes -pedantic -c -o vhcs_daemon.o vhcs_daemon.c
In file included from vhcs_daemon.c:2:
defs.h:11:20: error: stdlib.h: No such file or directory
defs.h:17:20: error: syslog.h: No such file or directory
defs.h:23:22: error: sys/stat.h: No such file or directory
defs.h:24:23: error: sys/types.h: No such file or directory
defs.h:25:24: error: sys/socket.h: No such file or directory
defs.h:31:24: error: netinet/in.h: No such file or directory
defs.h:37:22: error: sys/time.h: No such file or directory
defs.h:43:20: error: signal.h: No such file or directory
defs.h:49:20: error: string.h: No such file or directory
defs.h:55:19: error: errno.h: No such file or directory
defs.h:61:20: error: unistd.h: No such file or directory
defs.h:67:19: error: stdio.h: No such file or directory
defs.h:73:23: error: arpa/inet.h: No such file or directory
vhcs_daemon.c: In function ‘main’:
vhcs_daemon.c:12: error: storage size of ‘servaddr’ isn’t known
vhcs_daemon.c:15: error: storage size of ‘cliaddr’ isn’t known
vhcs_daemon.c:20: error: ‘pid_t’ undeclared (first use in this function)
vhcs_daemon.c:20: error: (Each undeclared identifier is reported only once
vhcs_daemon.c:20: error: for each function it appears in.)
vhcs_daemon.c:20: error: expected ‘;’ before ‘childpid’
vhcs_daemon.c:22: error: ‘socklen_t’ undeclared (first use in this function)
vhcs_daemon.c:22: error: expected ‘;’ before ‘clilen’
vhcs_daemon.c:27: error: ‘EOF’ undeclared (first use in this function)
vhcs_daemon.c:37: error: ‘LOG_DAEMON’ undeclared (first use in this function)
vhcs_daemon.c:39: warning: implicit declaration of function ‘socket’
vhcs_daemon.c:39: error: ‘AF_INET’ undeclared (first use in this function)
vhcs_daemon.c:39: error: ‘SOCK_STREAM’ undeclared (first use in this function)
vhcs_daemon.c:41: warning: implicit declaration of function ‘memset’
vhcs_daemon.c:41: warning: incompatible implicit declaration of built-in function ‘memset’
vhcs_daemon.c:41: error: ‘size_t’ undeclared (first use in this function)
vhcs_daemon.c:41: error: expected ‘)’ before ‘sizeof’
vhcs_daemon.c:45: warning: implicit declaration of function ‘htonl’
vhcs_daemon.c:47: warning: implicit declaration of function ‘htons’
vhcs_daemon.c:49: warning: implicit declaration of function ‘bind’
vhcs_daemon.c:50: warning: implicit declaration of function ‘strerror’
vhcs_daemon.c:50: error: ‘errno’ undeclared (first use in this function)
vhcs_daemon.c:50: warning: passing argument 2 of ‘say’ makes pointer from integer without a cast
vhcs_daemon.c:51: warning: implicit declaration of function ‘exit’
vhcs_daemon.c:51: warning: incompatible implicit declaration of built-in function ‘exit’
vhcs_daemon.c:54: warning: implicit declaration of function ‘listen’
vhcs_daemon.c:55: warning: passing argument 2 of ‘say’ makes pointer from integer without a cast
vhcs_daemon.c:56: warning: incompatible implicit declaration of built-in function ‘exit’
vhcs_daemon.c:61: warning: implicit declaration of function ‘calloc’
vhcs_daemon.c:61: warning: incompatible implicit declaration of built-in function ‘calloc’
vhcs_daemon.c:61: error: invalid application of ‘sizeof’ to incomplete type ‘struct timeval’ 
vhcs_daemon.c:62: error: invalid application of ‘sizeof’ to incomplete type ‘struct timeval’ 
vhcs_daemon.c:64: error: invalid application of ‘sizeof’ to incomplete type ‘struct timeval’ 
vhcs_daemon.c:66: error: invalid application of ‘sizeof’ to incomplete type ‘struct timeval’ 
vhcs_daemon.c:68: error: dereferencing pointer to incomplete type
vhcs_daemon.c:69: error: dereferencing pointer to incomplete type
vhcs_daemon.c:71: error: dereferencing pointer to incomplete type
vhcs_daemon.c:72: error: dereferencing pointer to incomplete type
vhcs_daemon.c:74: warning: implicit declaration of function ‘signal’
vhcs_daemon.c:74: error: ‘SIGCHLD’ undeclared (first use in this function)
vhcs_daemon.c:76: error: ‘SIGPIPE’ undeclared (first use in this function)
vhcs_daemon.c:79: error: ‘FILE’ undeclared (first use in this function)
vhcs_daemon.c:79: error: ‘file’ undeclared (first use in this function)
vhcs_daemon.c:79: warning: implicit declaration of function ‘fopen’
vhcs_daemon.c:80: warning: implicit declaration of function ‘fprintf’
vhcs_daemon.c:80: warning: incompatible implicit declaration of built-in function ‘fprintf’
vhcs_daemon.c:80: warning: implicit declaration of function ‘getpid’
vhcs_daemon.c:81: warning: implicit declaration of function ‘fclose’
vhcs_daemon.c:88: error: ‘clilen’ undeclared (first use in this function)
vhcs_daemon.c:88: error: expected ‘;’ before ‘sizeof’
vhcs_daemon.c:91: warning: implicit declaration of function ‘accept’
vhcs_daemon.c:99: error: ‘EINTR’ undeclared (first use in this function)
vhcs_daemon.c:103: warning: passing argument 2 of ‘say’ makes pointer from integer without a cast
vhcs_daemon.c:104: warning: incompatible implicit declaration of built-in function ‘exit’
vhcs_daemon.c:115: warning: implicit declaration of function ‘setsockopt’
vhcs_daemon.c:117: error: ‘SOL_SOCKET’ undeclared (first use in this function)
vhcs_daemon.c:118: error: ‘SO_RCVTIMEO’ undeclared (first use in this function)
vhcs_daemon.c:121: error: invalid application of ‘sizeof’ to incomplete type ‘struct timeval’ 
vhcs_daemon.c:126: error: ‘SO_SNDTIMEO’ undeclared (first use in this function)
vhcs_daemon.c:129: error: invalid application of ‘sizeof’ to incomplete type ‘struct timeval’ 
vhcs_daemon.c:133: warning: implicit declaration of function ‘inet_ntop’
vhcs_daemon.c:135: error: ‘childpid’ undeclared (first use in this function)
vhcs_daemon.c:135: warning: implicit declaration of function ‘fork’
vhcs_daemon.c:138: warning: implicit declaration of function ‘close’
vhcs_daemon.c:142: warning: implicit declaration of function ‘sprintf’
vhcs_daemon.c:142: warning: incompatible implicit declaration of built-in function ‘sprintf’
vhcs_daemon.c:148: warning: implicit declaration of function ‘free’
vhcs_daemon.c:150: warning: incompatible implicit declaration of built-in function ‘exit’
vhcs_daemon.c:156: warning: implicit declaration of function ‘closelog’
vhcs_daemon.c:15: warning: unused variable ‘cliaddr’
vhcs_daemon.c:12: warning: unused variable ‘servaddr’
make[2]: *** [vhcs_daemon.o] Error 1
make[2]: Leaving directory `/home/drndrw/Stuff/vhcs2-2.4.7.1/tools/daemon'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/drndrw/Stuff/vhcs2-2.4.7.1/tools'
make: *** [install] Error 2
```

I am also receiving an error. I didn't follow any of the steps, simply because they did not not work for me (the first one). I just ran the install and this is what happened.

---

### Post by eLinux on 2007-10-30
ok i have vhcs2 installed seems to all work fine everywhere. I go to test email and i can recieve email fine, but cant send i get this error

It was not possible to send this e-mail

so i look at vhcs2 diagnostics and logs and nothing else can be found any ideas?

---

### Post by Scimu on 2007-11-03
When I run the vhcs.sh as root, I get this error. By the way, this is the file I am running as root - [http://mirrors.penguinfriends.org/VHCS2/vhcs.sh](http://mirrors.penguinfriends.org/VHCS2/vhcs.sh).

Error:
```
root@server:/home/tom# sh vhcs.sh
vhcs.sh: 130: Syntax error: Bad substitution

```

I am running Ubuntu 7.10 server.

---

### Post by huwbie on 2007-11-05
Hey guys,

I've got VHCS running on my server perfectly fine, everything works (apart from the fact my emails aren't delievered to hotmail :p) 

However my filemanager in the backend of VHCS always returns the same error when i try to log in: Server Could Not Be Found.

Has anyone got any ideas as to why this is happening? 

Edit: I have narrowed it down to my FTP server never starting... i'm getting the following problem 

> ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.

Thanks & Regards

Huwbie

---

### Post by deejmer on 2007-11-13
Was wondering if anyone can help?  I have had VHCS2 up and running successfully for about a year, but am encountering an issue.  

Inside of my virtual hosts, if I create/upload files or directories via FTP, the owner is seen as "vu2007".  If a file or directory is uploaded/created by one of my PHP web applications (a CMS package) the owner is www-data (I assume from the default apache user).  

So if I try to manipulate/delete a vu2007 owned file through my web app, permissions don't allow it.  Same goes for the inverse transaction (FTP manipulation of a www-data owned file).  

Does anyone know how the 'www-data' user can be "dynamic" for each virtual host so that the owner matches no matter if the source of the file is from a PHP app or FTP?

I hope this makes sense.

---

### Post by razor7 on 2007-11-13
Please..install ISPConfig it is well maintained and there is a extensive howto on his installation process...

[www.ispconfig.com](www.ispconfig.com)

---

### Post by negru on 2007-11-25
i need help..im tring to install vhcs for a month by now..i tried averything...from debian to slackware...
now i found this ubuntu tutorial...
i tried the vhcs.sh  and i get this error

Unpacking mysql-server-4.1 (from .../mysql-server-4.1_4.1.15-1ubuntu5_i386.deb) ...
Aborting downgrade from (at least) 5.0 to 4.1.
dpkg: error processing /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ERROR # 100 : There was an error installing required package

---

### Post by firewren on 2007-12-04
> **Scimu said:**
> When I run the vhcs.sh as root, I get this error. By the way, this is the file I am running as root - [http://mirrors.penguinfriends.org/VHCS2/vhcs.sh](http://mirrors.penguinfriends.org/VHCS2/vhcs.sh).

Error:
```
root@server:/home/tom# sh vhcs.sh
vhcs.sh: 130: Syntax error: Bad substitution

```

I am running Ubuntu 7.10 server.

Follow the instructions on this page [http://mirrors.penguinfriends.org/VHCS2/#en](http://mirrors.penguinfriends.org/VHCS2/#en) not those located at the VHCS website and you shouldn't see that error.

---

### Post by winlinfix on 2007-12-28
i am unable to find dns configuration and dns management option in vhcs2

how to add dns for domain and how to manage dns in vhcs2?

---

### Post by ruben0 on 2008-03-17
<blank> stupid question - found the answer

---

### Post by masterkiller on 2008-04-23
hi guys thought this maybe of some help
now all we need to do is apt-get to install it 
[http://vhcs.net/new/modules/news/article.php?storyid=24](http://vhcs.net/new/modules/news/article.php?storyid=24)

---

### Post by Dymocaptin on 2008-06-11
Hey guys. So I'm having some problems trying to get this thing installed correctly. I get all the way up to where you actually setup VHCS.

After running this it says that It cannot find vhcs2.conf. I tried manually moving it there, but no luck.

sudo /var/www/vhcs2/engine/setup/vhcs2-setup

When I try to run the automatic script, it doesn't ever let me accept the terms. I hit Y, Yes and everything in between. I've done alittle with linux before, but never anything really in depth. If you could dumb down your answers to this it would be awesome!

---

### Post by Dymocaptin on 2008-06-11
After installing the packages it gives me an error when I try to run
apt-get install vhcs saying:

```
vhcs: Depends: vhcs-gui (= 2.4.7.1-2) but it is not going to be installed
E: Broken packages
```

Anyone wanna help?


Latest packages installed(deb [http://apt.scunc.org/](http://apt.scunc.org/) sarge main)

```
# aptitude install ssh postfix postfix-tls proftpd proftpd-mysql \
courier-authdaemon courier-base courier-imap courier-maildrop \
courier-pop libberkeleydb-perl libcrypt-blowfish-perl libcrypt-cbc-perl \
libcrypt-passwdmd5-perl libdate-calc-perl libdate-manip-perl \
libdbd-mysql-perl libdbi-perl libio-stringy-perl libmail-sendmail-perl \
libmailtools-perl libmd5-perl libmime-base64-perl libmime-perl \
libnet-dns-perl libnet-netmask-perl libnet-perl libnet-smtp-server-perl \
libperl5.8 libsnmp-session-perl libterm-readkey-perl libtimedate-perl perl \
perl-base perl-modules bind9 diff gzip iptables libmcrypt4 php4 patch php4-mcrypt \ php4-mysql php4-pear procmail tar original-awk libterm-readpassword-perl \ libsasl2-modules libsasl2 sasl2-bin bzip2 gcc make libc6-dev mysql-client-4.1 \ mysql-server-4.1 apache2 apache2-common apache2-mpm-prefork \ libapache2-mod-php4
```

---

### Post by Mahod on 2008-07-04
hello

my Server install the Vhcs but Error

this error

> root@serv:~/vhcs2.4# make install
cd ./tools && make install
make[1]: Entering directory `/root/vhcs2.4/tools'
cd ./build && make install 
make[2]: Entering directory `/root/vhcs2.4/tools/build'
cp ./vhcs2-mkdirs.pl /usr/sbin
make[2]: Leaving directory `/root/vhcs2.4/tools/build'
cd ./daemon && make vhcs2_daemon
make[2]: Entering directory `/root/vhcs2.4/tools/daemon'
make[2]: `vhcs2_daemon' is up to date.
make[2]: Leaving directory `/root/vhcs2.4/tools/daemon'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/daemon
cp ./daemon/vhcs2_daemon /tmp/vhcs2.4/var/www/vhcs2/daemon 
make[1]: Leaving directory `/root/vhcs2.4/tools'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/etc/vhcs2
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/log/vhcs2
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/virtual
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/mail/virtual
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/log/apache2/backup
cd ./configs && make install 
make[1]: Entering directory `/root/vhcs2.4/configs'
if [[ debian == debian ]] ; then \
                cp ./vhcs2.conf /tmp/vhcs2.4/etc/vhcs2 ; \
                cd ./apache && make install ; cd .. ; \
                cd ./bind && make install ; cd .. ; \
                cd ./crontab && make install ; cd .. ; \
                cd ./database && make install ; cd .. ;  \
                cd ./init.d && make install ; cd .. ; \
                cd ./postfix && make install ; cd .. ; \
                cd ./courier && make install ; cd .. ; \
                cd ./proftpd && make install ; cd .. ; \
        fi
/bin/sh: [[: not found
make[1]: Leaving directory `/root/vhcs2.4/configs'
cd ./engine && make install 
make[1]: Entering directory `/root/vhcs2.4/engine'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/backup
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/quota
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/traffic
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/messager
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/setup
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/tools
cd ./traffic && make install
make[2]: Entering directory `/root/vhcs2.4/engine/traffic'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/usr/sbin
cp  ./pflogsumm-1.1.0/pflogsumm.pl /tmp/vhcs2.4/usr/sbin
make[2]: Leaving directory `/root/vhcs2.4/engine/traffic'
cp -p -R ./vhcs2_common_code.pl /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-rqst-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-dmn-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-sub-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-als-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-htuser-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-mbox-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-serv-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-db-passwd /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./backup/vhcs2-bk-task /tmp/vhcs2.4/var/www/vhcs2/engine/backup
cp -p -R ./backup/vhcs2-backup-all /tmp/vhcs2.4/var/www/vhcs2/engine/tools
cp -p -R ./quota/vhcs2-dsk-quota /tmp/vhcs2.4/var/www/vhcs2/engine/quota
cp -p -R ./traffic/vhcs2-srv-traff /tmp/vhcs2.4/var/www/vhcs2/engine/traffic
cp -p -R ./traffic/vhcs2-vrl-traff /tmp/vhcs2.4/var/www/vhcs2/engine/traffic
cp -p -R ./messager/vhcs2-arpl-msgr /tmp/vhcs2.4/var/www/vhcs2/engine/messager
cp -p -R ./setup/vhcs2-setup /tmp/vhcs2.4/var/www/vhcs2/engine/setup
cp -p -R ./setup/vhcs2-uninstall /tmp/vhcs2.4/var/www/vhcs2/engine/setup
cp -p -R ./tools/vhcs2-httpd-logs-mngr /tmp/vhcs2.4/var/www/vhcs2/engine/tools/vhcs2-httpd-logs-mngr
cp -p -R ./setup/vhcs2-cfg-subst /tmp/vhcs2.4/var/www/vhcs2/engine/setup
make[1]: Leaving directory `/root/vhcs2.4/engine'
cd ./gui && make install 
make[1]: Entering directory `/root/vhcs2.4/gui'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/gui
cp ./index.php /tmp/vhcs2.4/var/www/vhcs2/gui/index.php
cp ./chk_login.php /tmp/vhcs2.4/var/www/vhcs2/gui/chk_login.php
cp -dR ./admin /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./reseller /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./client /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./include /tmp/vhcs2.4/var/www/vhcs2/gui
rm -rf /tmp/vhcs2.4/var/www/vhcs2/gui/{admin,reseller,client,include}/Makefile
cp -dR ./domain_default_page /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./errordocs /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./images /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./themes /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./tools /tmp/vhcs2.4/var/www/vhcs2/gui
make[1]: Leaving directory `/root/vhcs2.4/gui'


---

### Post by streetoast on 2008-12-01
DO NOT USE VHCS (or get your server hacked), see:

[http://ubuntu-tutorials.com/2006/08/15/vhcs-v2471-pro-do-not-use/](http://ubuntu-tutorials.com/2006/08/15/vhcs-v2471-pro-do-not-use/)

---

### Post by razor7 on 2008-12-01
Yes, please install the Free ISP Config software [http://www.ispconfig.org/](http://www.ispconfig.org/) that comes with native Ubuntu support...it really rocks!

Best regards to all!

---

### Post by CGSBNetworks on 2009-04-27
Hi,
 
I'm also having problems with proftpd.
 
Everything else is working except that after a user creates a ftp account, they then cannot use it because the password is incorrect?
 
Any ideas?

---

### Post by own3mall on 2009-07-07
How do I get VHCS to work on Ubuntu 9.04?

E: Broken packages
root@eric-desktop:~# apt-get install vhcs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vhcs: Depends: vhcs-gui (= 2.4.7.1-2) but it is not going to be installed
        PreDepends: proftpd-mysql (>= 1.2.8) but it is not installable
        PreDepends: libperl5.8 but it is not installable
        PreDepends: libconfhelper-perl but it is not installable
E: Broken packages
root@eric-desktop:~# 

Not sure what to do...

---

### Post by dforge on 2009-07-07
VHCS looks great, but it hasn't been updated in years. It's best to avoid it and use alternatives.

---

