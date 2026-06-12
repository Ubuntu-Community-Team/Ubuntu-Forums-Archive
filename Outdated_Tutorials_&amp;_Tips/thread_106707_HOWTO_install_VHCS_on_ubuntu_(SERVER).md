---
title: "HOWTO: install VHCS on ubuntu (SERVER)"
date: 2005-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2005-12-21
**N.B: a maintained version of this howto can be found [here](http://wael.nasreddine.com/Articles/Articles/Install_VHCS_on_Ubuntu_%10_Debian.html)**

Hello,
**Q.what is VHCS?**
[vhcs](http://www.vhcs.net) (Virtual Hosting Control System) is a software solution to run a webserver, mailserver, DNSserver, FTP server on linux (the current supported OS for now)

**Q.How to install it**
Just follow the HOWTO below:

First begin by instaling ubuntu (don't need to choose server option, i will give you solutions to tweak it also, but if you don't want to use X at all then choose server).. after ubuntu is installed, Do the following:

Now you have the solution to either install it manually by following the silver text down there or follow the automatic method below:
```

wget http://wael.nasreddine.com/files/vhcs/vhcs.sh

```

now type
```

sudo -s -H
<enter password>
sh vhcs.sh

```

and follow the inline instructions

[COLOR=Red]
NOTE: You are not authorised to modify/remove the license that is inside the script 2 times, it's 15 line and must be always the same 15 line, but you can modify the script and/or redestribute it without changing those licence lines, thank you[/COLOR]

[COLOR=Silver]0. make sure you have all needed repository, tested with /etc/apt/sources.list
```

#ubuntu archive
deb http://fr.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

# ubuntu updates
deb http://fr.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

#ubuntu security
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

```

1-making temp directories (you can change them to anything but we just need a folder to drop the files in it to make vhcs)
```

sudo mkdir /tmp/vhcs_tmp
sudo mkdir /tmp/vhcs_tmp/install
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

sudo apt-get install -assume-yes --force-yes ssh postfix postfix-tls proftpd-mysql courier-authdaemon courier-base courier-imap courier-maildrop courier-pop libberkeleydb-perl libcrypt-blowfish-perl libcrypt-cbc-perl libcrypt-passwdmd5-perl libdate-calc-perl libdate-manip-perl libdbd-mysql-perl libdbi-perl libio-stringy-perl libmail-sendmail-perl libmailtools-perl libmd5-perl libmime-perl libnet-dns-perl libnet-netmask-perl libnet-perl libnet-smtp-server-perl libperl5.8 libsnmp-session-perl libterm-readkey-perl libtimedate-perl perl perl-base perl-modules bind9 diff gzip iptables libmcrypt4 mysql-client mysql-common mysql-server patch php4 php4-mcrypt php4-mysql php4-pear procmail tar original-awk libterm-readpassword-perl libsasl2-modules libsasl2 sasl2-bin apache2 apache2-common apache2-mpm-prefork libapache2-mod-php4 bzip2


```

6-getting vhcs archive file from vhcs.net (this is for the current 2.4.6.2version, visit [http://www.vhcs.net](http://www.vhcs.net) for the current/latest version)

7-exctracting the archive, and entering into the vhcs sources directory
```

tar xjvf vhcs2.4.tar.bz2
cd ./vhcs2

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

3. restart proftpd
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
Open /etc/vhcs2/apache/parts/{prefix}_entry.tpl where {prefix} is "als", "dmn" and "sub" without quotes
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
1.0 [ 21-12-2005 ] First Version Imported from my [hoary script](http://ubuntuforums.org/showthread.php?t=25722)
[/COLOR]

---

### Post by Gandalf on 2005-12-31
Script updated to install latest VHCS 2.4.7

---

### Post by tariqf on 2006-01-16
Hi will you be able to update your script to install version 2.4.7.1? There a few bad bugs in 2.4.7 that this update fixes.

---

### Post by Gandalf on 2006-01-16
[QUOTE=tariqf]Hi will you be able to update your script to install version 2.4.7.1? There a few bad bugs in 2.4.7 that this update fixes.[/QUOTE]
HUH? What u're talking about man? haven't u checked the script?
the script was updated to install VHCS2.4.7.1 the night 2.4.7.1 was released, plus an upgrade 2.4.7 -> 2.4.7.1 was included, i just didn't update this topic, please next time take a look to the script before asking :D

---

### Post by tariqf on 2006-01-17
Sorry Gandalf I should have checked the script. Many thanks for such a handy piece of code.

Tariq

---

### Post by Gandalf on 2006-01-17
[QUOTE=tariqf]Sorry Gandalf I should have checked the script. Many thanks for such a handy piece of code.

Tariq[/QUOTE]
u're welcome :D and don't worry its ok :D

---

### Post by Zelut on 2006-01-20
I am currently running ISPConfig for my hosting service.  Can anyone give me a comparison of the two?  I'd be willing to try another if it is well supported & configurable.

---

### Post by hen3rz on 2006-01-21
> I am currently running ISPConfig for my hosting service. Can anyone give me a comparison of the two? I'd be willing to try another if it is well supported & configurable.

Im also interested. I have read up tutorials about how to install both of these and em currently at a cross roads about which one to pick. If anyone has tried out both ISPConfig and VHCS could you please give ur oppinion about how these two compare against each other.

---

### Post by Gandalf on 2006-01-21
I think the [demo](http://vhcs.net/new/modules/wfchannel/index.php?pagenum=7) speek for itself, i can't compare coz i never used ISPconfig but from what i see on the demo, it's not as good as VHCS is!

---

### Post by Zelut on 2006-01-28
I'm hoping someone can help me with this.  I just followed a migration howto to move my VHCS back to my production server.  Everything works except for smtp.  Any ideas?  This is what I used

[www.billboardhosting.com/vhcs2_migrate.txt](www.billboardhosting.com/vhcs2_migrate.txt)

VHCS status shows SMTP OFF.  How can I make sure this is active & open on my ubuntu installation?  Thanks

---

### Post by heislord5 on 2006-04-16
please help,

My email server worked at first, and now it just doesn't send mail.  It accepts, but doesn't send....ok let me rephrase...it says it sends but it never arrives on the other side.  Servers say they both are up.  I'm using zoneedit, because I have dynamic ip.

Why would mail come in but not get out?  What records do I need in the A-record and MX record fields?

my domain is predestine.org

I've tried dnsreport with a variety of zoneedit dns settings, but the ones I know worked before was having an A record:
mail.predestine.org    11.11.11.11 (substitute ip)
but no MX record.

later I added MX record and I think it was working for a while.
mail.predestine.org {handles mail for} predestine.org

Just after a while, it stopped working.  I'm going to try removing the MX record again...but dnsreports says that is bad and the zoneedit people also said I needed it.

---

### Post by heislord5 on 2006-04-17
I completely reinstalled...no change.

---

### Post by heislord5 on 2006-04-17
I see the following when doing dnsreports report:

WARNING: One or more of your mailservers is claiming to be a host other than what it really is (the SMTP greeting should be a 3-digit code, followed by a space or a dash, then the host name). If your mailserver sends out E-mail using this domain in its EHLO or HELO, your E-mail might get blocked by anti-spam software. This is also a technical violation of RFC821 4.3 (and RFC2821 4.3.1). Note that the hostname given in the SMTP greeting should have an A record pointing back to the same server.

mail.predestine.org claims to be invalid hostname 'bradsserver':
   220 bradsserver VHCS2 2.4 Spartacus Managed ESMTP 2.4.7.1

---

### Post by heislord5 on 2006-04-17
at command prompt I do (don't know if this is right:

telnet mx2.hotmail.com 25

I get as a result:
Trying 65.54.244.40...
Trying 65.54.244.168...
Trying 65.54.245.40...
Trying 65.54.190.50...
telnet: Unable to connect to remote host: Connection timed out

.
.
.
turns out my isp was blocking port 25.  I got them to open it.  Now I can't ftp files...I was able to do this before.  I recontacted them and they said they don't block port 21.  DNS resolves and ftp client says it's connecting to my ip port 21.  But then it says couldn't log in.  I tried the same name and password that I setup specifically for ftp on the domain from vhcs.  I tried both with and without the domain on the end.  Any hints?

---

### Post by gymsmoke on 2006-04-17
After several tries with a number of control panel/cms solutions, I am thoroughly convinced that there is no substitute for just taking the time to "know how" to configure the components for a server, instead of allowing these packages to do the work for you.  I've personally setup and used plex, adminpanel, cpanel, and ispconfig.  I've documented the installation and config of ispconfig on the forums at howtoforge, and, after finding bugs and inconsistencies with the install/configuration, have heard nothing back from the developers.  I've also seen the havoc that can be caused on a server when these user applications go wrong...

My recommendation is to leave them alone, learn how to configure mail/dns/apache/mysql, or host with an isp who will do this for you, since it is most likely that, when you get stuck, no one will be around to answer your questions in a manner that will really help.

---

### Post by heislord5 on 2006-04-17
gymsmoke,

I appreciate your reply.  I would say that I partially agree....even more than half agree.  Most of the time, it's good to be able to handle the things going on behind the scenes oneself.  Maybe even most of the time it's best, but it's not always best.  I'm a firm believer in abstraction.  I've seen how far it has taken programming languages.  I mean, just think about how bijection will affect Java over the next few years...being able to just tell the application server "Hey, handle these security, threading and persistence issues for me."  Sometimes abstraction is a very beautiful thing.  Every time we get in a car, watch a tv, live in a house, wear cloths, do just about anything, we are taking advantage of a certain level of abstraction.  I don't have to know how to sew to wear cloths...it would be great if I did.  Then when I got a tear, I could fix it myself.  But for the many people, relegating those cloths to yardwork and purchasing a new outfit might be a better choice so that they can maintain the beauty of abstraction.

For me I need to learn this stuff in and out...but I want to take it small pieces at a time.  I will be looking into the details over time, just right now I just want it to run.  I'm a programmer, and that's part of the reason I'm getting into this...but a little at a time is ok.  In plus, building something equivalent to this system would take forever because this represents the work of a lot of people and a lot of man-hours.  If we all have to reinvent the wheel, we'll never make progress.  I'd rather just stand on the top of giants that came before and maybe add one inch to the stack for the next guy to stand on.

BTW - I've discovered that I can't get to the file manager through the filemanager link...says can't find server.  Server status says ftp server is up (as does the system->administration->services.  I unchecked, closed, checked again and closed again...that should bring it down and back up right?  Same result.  Filemanager, and other Ftp clients can't find the ftp server....significant that even internal to the app it can't be found, except on the status page where it says its up.

---

### Post by Zelut on 2006-04-21
Hey everybody.  I've been running vhcs for some months now & its been great for my small hosting company.

Recently I've tried to add domain alias or subdomains and it isn't quite working.  I've got the DNS setup correctly as the subdomain.domain.tld will connect, but it displays the content from the main domain.

I've removed the *.domain.tld from the ServerAlias line & there is a <VirtualHost> entry for the subdomain.domain.tld.  Any suggestions?

---

### Post by newpants2003 on 2006-06-17
#5 is stil not working for me.
i got error:   E: Command line option ‘a’ [from -assume-yes] is not known.
when i follow the automatic method i got error:
    .
    .
    .
    .
 
libterm-readkey-perl is already the newest version.
libtimedate-perl is already the newest version.
perl is already the newest version.
perl-base is already the newest version.
perl-modules is already the newest version.
diff is already the newest version.
gzip is already the newest version.
iptables is already the newest version.
Package mysql-common-4.1 is a virtual package provided by:
  mysql-common 5.0.22-0ubuntu6.06
You should explicitly select one to install.
E: Package mysql-common-4.1 has no installation candidate
ERROR # 100 : There was an error installing required packages.

what i did wrong?

---

### Post by newpants2003 on 2006-06-17
and error like:


The following packages have unmet dependencies.
  libdbd-mysql-perl: Depends: libmysqlclient15off (>= 5.0.19-1) but it is not going to be installed
  mysql-client-4.1: Depends: mysql-common (>= 4.1.15-1ubuntu5)
                    Depends: libmysqlclient14 (>= 4.1.15-1ubuntu5) but it is not going to be installed
                    Depends: libmysqlclient14 but it is not going to be installed
  mysql-server-4.1: Depends: mysql-common (>= 4.1.15-1ubuntu5)
                    Depends: libmysqlclient14 but it is not going to be installed
  php4-mysql: Depends: libmysqlclient15off (>= 5.0.19-1) but it is not going to be installed
  proftpd-mysql: Depends: libmysqlclient15off (>= 5.0.19-1) but it is not going to be installed
E: Broken packages
ERROR # 100 : There was an error installing required packages.

---

### Post by Gandalf on 2006-06-17
[QUOTE=newpants2003]and error like:


The following packages have unmet dependencies.
  libdbd-mysql-perl: Depends: libmysqlclient15off (>= 5.0.19-1) but it is not going to be installed
  mysql-client-4.1: Depends: mysql-common (>= 4.1.15-1ubuntu5)
                    Depends: libmysqlclient14 (>= 4.1.15-1ubuntu5) but it is not going to be installed
                    Depends: libmysqlclient14 but it is not going to be installed
  mysql-server-4.1: Depends: mysql-common (>= 4.1.15-1ubuntu5)
                    Depends: libmysqlclient14 but it is not going to be installed
  php4-mysql: Depends: libmysqlclient15off (>= 5.0.19-1) but it is not going to be installed
  proftpd-mysql: Depends: libmysqlclient15off (>= 5.0.19-1) but it is not going to be installed
E: Broken packages
ERROR # 100 : There was an error installing required packages.[/QUOTE]
No one else got such errors, can you please purge any already and needed package and retry again ?

---

### Post by newpants2003 on 2006-06-17
how to do that? remove all the files i installed?

---

### Post by newpants2003 on 2006-06-17
is there something wrong with step 5 ?

#5 is stil not working for me.
i got error:
 E: Command line option ‘a’ [from -assume-yes] is not known.

---

### Post by YorYor on 2006-07-27
Not sure if anyone has tried to replace the php4 and mysql*4.1 with the newer versions of php5 and mysql*5 (i.e. removing the 4.1) on Dapper?
Trying it now... will update to see if it works fine.

---

### Post by Gandalf on 2006-07-27
> **YorYor said:**
> Not sure if anyone has tried to replace the php4 and mysql*4.1 with the newer versions of php5 and mysql*5 (i.e. removing the 4.1) on Dapper?
Trying it now... will update to see if it works fine.
I use php5 and mysql5 -> [http://wael.nasreddine.com/phpinfo.php](http://wael.nasreddine.com/phpinfo.php) but I don't run ubuntu nor debian, I run my own distribution, The reason i kept vhcs.sh use php/mysql 4 is coz before dapper was out, there was no php5-mcrypt package, now there is one but only for dapper, Also I'm saying it should in theory but I appreciate it if you replace all php4 with php5 and mysql4 with mysql5 and install on a **fresh** ubuntu installation, If everything is ok, i'll update my script

---

### Post by YorYor on 2006-07-28
I think so far everything is ok on Dapper. I've not done extensive testing yet, but adding resellers and customers seem to be ok.
I'll be testing it more over the next few days... perhaps someone could also try in parallel.

Only thing to note is the php-pear package... instead of php4-pear or php5-pear.

Is there any way you can make your script detect the distro, and if Dapper use 5 else use 4?

Also, I think it would be advisable to automatically install libapache2-mod-chroot and perhaps giving users running the script the option of enabling it?
sudo ln -s /etc/apache2/mods-available/mod_chroot.load /etc/apache2/mods-enabled/ (I'm sure you already know this)

*Note*
======
As mentioned in this reply by serkanhamarat ([http://www.ubuntuforums.org/showthread.php?t=25722&page=13)](http://www.ubuntuforums.org/showthread.php?t=25722&page=13)), there is an error with the webmail script /var/www/vhcs2/gui/tools/webmail/inc/inc.php line 153-155. One needs to change from:

```
Header("Expires: Wed, 11 Nov 1998 11:11:11 GMT\r\n".
"Cache-Control: no-cache\r\n".
"Cache-Control: must-revalidate");
```

to:

```
Header("Expires: Wed, 11 Nov 1998 11:11:11 GMT");
Header("Cache-Control: no-cache");
Header("Cache-Control: must-revalidate");
```

---

### Post by Gandalf on 2006-07-28
> **YorYor said:**
> I think so far everything is ok on Dapper. I've not done extensive testing yet, but adding resellers and customers seem to be ok.
I'll be testing it more over the next few days... perhaps someone could also try in parallel.
 can you please put a phpinfo(); file and send me a link (here or in private) to see if everything normal, and yes please do more tests
> **YorYor said:**
> 
Only thing to note is the php-pear package... instead of php4-pear or php5-pear.
 Thx for pointing this out, will save me a lot of time since I don't have any ubuntu installation ATM
> **YorYor said:**
> 
Is there any way you can make your script detect the distro, and if Dapper use 5 else use 4?
 that's already done, the script will install on Ubuntu breezy, Ubuntu dapper and debian (general)
> **YorYor said:**
> 
Also, I think it would be advisable to automatically install libapache2-mod-chroot and perhaps giving users running the script the option of enabling it?
sudo ln -s /etc/apache2/mods-available/mod_chroot.load /etc/apache2/mods-enabled/ (I'm sure you already know this)
 I don't go this deep actually, I leave all that to the user option, the script's job is to give the user a VHCS installation ready for buisness in a few clicks, also I extended it later to install what we called Hacks, but i'm not planning to go any deeper than that
> **YorYor said:**
> 
*Note*
======
As mentioned in this reply by serkanhamarat ([http://www.ubuntuforums.org/showthread.php?t=25722&page=13)](http://www.ubuntuforums.org/showthread.php?t=25722&page=13)), there is an error with the webmail script /var/www/vhcs2/gui/tools/webmail/inc/inc.php line 153-155. One needs to change from:

```
Header("Expires: Wed, 11 Nov 1998 11:11:11 GMT\r\n".
"Cache-Control: no-cache\r\n".
"Cache-Control: must-revalidate");
```

to:

```
Header("Expires: Wed, 11 Nov 1998 11:11:11 GMT");
Header("Cache-Control: no-cache");
Header("Cache-Control: must-revalidate");
```
Okay i will verify it, and add it to the patches section in the script, thx

---

### Post by YorYor on 2006-07-28
Seems like vhcs2 doesn't quite like mod_chroot... I will have to figure it out again all the necessary hacks in order to make vhcs2 operate in a jail environment.
Or does someone else already know how to? Please share it!

This is the phpinfo I extracted from my trial vhcs server and placed it on a live server.
[http://conceptlane.com/projects/phpinfo.html]("http://conceptlane.com/projects/phpinfo.html")
Looks pretty alright to me... will wait to hear from you.

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

### Post by Brueggi on 2006-08-06
Hi Gandalf!

I just tried do install VHCS by using your script, but it seems like the server is down.

I can still ping wael.nasreddine.com and access it by FTP but I always get "Connection reset by peer" when I try to access it by HTTP.
Maybe you could solve this problem... ;) 

Brueggi

---

### Post by godlike on 2006-10-03
Does anyone else have a copy of the script? The site has been down for a few days at least

---

### Post by phizz on 2006-10-04
I wounder if they've fixed the gaping security hole? I was testing with a dmz box and she got hit hard. Nothing done to it just defaced.

---

### Post by serkanhamarat on 2006-10-09
Gandalf are you aware? Your site doesn't seem to same old anymore... :confused:

---

### Post by heymrdj on 2006-10-16
> **serkanhamarat said:**
> Gandalf are you aware? Your site doesn't seem to same old anymore... :confused:

Yeah, I wish I could find the .sh script as well. I was wondering if someone could help me figure out how I need to configure this thing.

I'm trying to get it to point to my IP I have set up through no-ip.com for redirection. I'm trying to get the server to run as [www.everythinganime.no-ip.com](www.everythinganime.no-ip.com) (strictly a test center for the .org main site). I use cpanel for the server in my datacenter, but I have this old computer so I wanna use VHCS on it for testing scripts.

Anyways, I don't know how to go about getting the internal IP of 192.168.0.6 to get connected to the no-ip system.

More importantly, whenever I install this thing, I ALWAYS get a MySQL can't connect error. I am prepared to uninstall my Dapper Drake and redo all the installations. But what i need is a better method of setup, I'm screwing up somewhere, just can't figure how. ](*,)

---

### Post by razor7 on 2006-10-16
Hello...go to [http://vhcs.net/new/modules/newbb/viewtopic.php?topic_id=4315&viewmode=flat&order=ASC&start=78](http://vhcs.net/new/modules/newbb/viewtopic.php?topic_id=4315&viewmode=flat&order=ASC&start=78), there are some instructions to install VHCS using debian packages, it works on ubuntu 6.06 anb 6.10 beta!!! Just look at [www.mgsconectiva.com.ar](www.mgsconectiva.com.ar).


For the dynamic IP look at [www.cdmon.com....the](www.cdmon.com....the) offer DynDNS support for free.


Regards.

---

### Post by heymrdj on 2006-10-17
Thx alot razor. I'll give the script in that topic a try tonight. Currently reimaging my server cause I apparently screwed up the mysql and a few other things fooling with it last night. Royally screwed the DNS system...


BTW that link going to like cdmon doesn't work cause the forum autimatically shortens it, so its like [www.cdmon.co......the](www.cdmon.co......the)    Try taking your url and wrapping it in the url tags.

---

### Post by serkanhamarat on 2006-10-18
[COLOR="DarkRed"]WARNING[/COLOR]

Who upgrades proftpd to version 1.3.0,
and gets problems with FTP login like
```
 421 Service not available, remote server has closed connection 
```
disable TLS/SSL modules from /etc/proftpd/modules.conf
because of such old ftp clients cannot communicate.

Also you can disable radius and postgres style auth-mechanisms
that unused with VHCS.

All these modules comes enabled in dapper by default.

---

### Post by heymrdj on 2006-10-18
> **serkanhamarat said:**
> [COLOR="DarkRed"]WARNING[/COLOR]

Who upgrades proftpd to version 1.3.0,
and gets problems with FTP login like
```
 421 Service not available, remote server has closed connection 
```
disable TLS/SSL modules from /etc/proftpd/modules.conf
because of such old ftp clients cannot communicate.

Also you can disable radius and postgres style auth-mechanisms
that unused with VHCS.

All these modules comes enabled in dapper by default.

The install is no good. When I try to run apt-get install VHCS I get a bunch of dependency warnings. 

```
root@server1:/# apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Ign http://apt.scunc.org sarge Release.gpg
Get:2 http://apt.scunc.org sarge Release
Get:3 http://apt.scunc.org sarge/main Packages [4773B]
Get:4 http://apt.scunc.org sarge/main Sources [1443B]
Get:5 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:6 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Fetched 6219B in 1m28s (70B/s)
Reading package lists... Done
root@server1:/# apt-get install vhcs
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vhcs: Depends: vhcs-gui (= 2.4.7.1-2) but it is not going to be installed
        PreDepends: libcrypt-cbc-perl but it is not installable
        PreDepends: proftpd-mysql (>= 1.2.8) but it is not installable
        PreDepends: courier-maildrop but it is not installable
        PreDepends: libdbd-pg-perl but it is not installable
        PreDepends: libcrypt-passwdmd5-perl but it is not installable
        PreDepends: pflogsumm but it is not installable
        PreDepends: libberkeleydb-perl but it is not installable
        PreDepends: libdate-calc-perl but it is not installable
        PreDepends: libmd5-perl but it is not installable
        PreDepends: libnet-netmask-perl but it is not installable
        PreDepends: libnet-smtp-server-perl but it is not installable
        PreDepends: libterm-readkey-perl but it is not installable
        PreDepends: libterm-readpassword-perl but it is not installable
        PreDepends: libconfhelper-perl but it is not installable
E: Broken packages
root@server1:/#
```

Any ideas. I REALLY need this to work. :(

---

### Post by razor7 on 2006-10-18
> **heymrdj said:**
> Thx alot razor. I'll give the script in that topic a try tonight. Currently reimaging my server cause I apparently screwed up the mysql and a few other things fooling with it last night. Royally screwed the DNS system...


BTW that link going to like cdmon doesn't work cause the forum autimatically shortens it, so its like [www.cdmon.co......the](www.cdmon.co......the)    Try taking your url and wrapping it in the url tags.

The dynamic DNS service is at [www.cdmon.com](www.cdmon.com)

Also I have found this great tutorial on installing VHCS using debian packages, with screenshots and more...

[http://www.debianadmin.com/vhcs-isp-control-panel-installation-with-screenshots.html](http://www.debianadmin.com/vhcs-isp-control-panel-installation-with-screenshots.html)

---

### Post by heymrdj on 2006-10-19
> **razor7 said:**
> The dynamic DNS service is at [www.cdmon.com](www.cdmon.com)

Also I have found this great tutorial on installing VHCS using debian packages, with screenshots and more...

[http://www.debianadmin.com/vhcs-isp-control-panel-installation-with-screenshots.html](http://www.debianadmin.com/vhcs-isp-control-panel-installation-with-screenshots.html)

Looks good, I'll give it a try tonight.

Any idea what part to change in that if I wanna assign it the LAN IP of 192.168.0.6?

---

### Post by razor7 on 2006-10-19
> **heymrdj said:**
> Looks good, I'll give it a try tonight.

Any idea what part to change in that if I wanna assign it the LAN IP of 192.168.0.6?

you have to register, add some domains on your own and download the applications that automatically reload your account in CDMON with you cuyrrent public IP.

---

### Post by heymrdj on 2006-10-19
Ok i see. But I'll still have to use no-ip because I don't understand enough spanish to work with CDMON. Thx for the help though. :)

---

### Post by heymrdj on 2006-10-19
```
root@server1:/home/heymrdj/noip/noip-2.1.3# apt-get install vhcs
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vhcs: Depends: vhcs-gui (= 2.4.7.1-2) but it is not going to be installed
        PreDepends: libcrypt-cbc-perl but it is not installable
        PreDepends: proftpd-mysql (>= 1.2.8) but it is not installable
        PreDepends: courier-maildrop but it is not installable
        PreDepends: libdbd-pg-perl but it is not installable
        PreDepends: libcrypt-passwdmd5-perl but it is not installable
        PreDepends: pflogsumm but it is not installable
        PreDepends: libberkeleydb-perl but it is not installable
        PreDepends: libdate-calc-perl but it is not installable
        PreDepends: libmd5-perl but it is not installable
        PreDepends: libnet-netmask-perl but it is not installable
        PreDepends: libnet-smtp-server-perl but it is not installable
        PreDepends: libterm-readkey-perl but it is not installable
        PreDepends: libterm-readpassword-perl but it is not installable
        PreDepends: libconfhelper-perl but it is not installable
E: Broken packages

```

I get it again. Why can't it find these packages? I'm using 6.06 just like you. Is it because I'm using Kubuntu? surely using KDE wouldn't be the cause. I tried using synaptic and it gives me the same dependency errors.

When i try to download one manually this is what I typically get.

```
 apt-get install libcrypt-cbc-perl
Reading package lists... Done
Building dependency tree... Done
Package libcrypt-cbc-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libcrypt-cbc-perl has no installation candidate

```

---

### Post by heymrdj on 2006-10-19
Nevermind, my brother showed me how to enable the UN-AUTHENTICATED servers in the synaptic repositories. That got it right there :). I'm attempting an install now. its currently downloading.

---

### Post by dxlwebs on 2009-03-22
hello how would i enable the un-authenticated servers?

---

