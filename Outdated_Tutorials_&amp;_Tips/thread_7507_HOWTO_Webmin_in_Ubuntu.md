---
title: "HOWTO: Webmin in Ubuntu"
date: 2004-12-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Readis on 2004-12-08
First of all, and most important... _DON'T_ use the webmin from apt-get or Synaptic.  These are older files, and they will require 'root' as the login.  I know, I know... there are ways to login as root, and use root access, but why deal with it?  Here is what I have done, and it is much more secure then what you will get with their packages.

Prereqs: Perl 5 interpreter (Should be installed with base system)
               libnet-ssleay-perl ( Not install with base system... get with Synaptic)

Download 'webmin-1.170.tar.gz' from [www.webmin.com/download.html](www.webmin.com/download.html)
-------
cd (location you downloaded to)
sudo tar xzvf webmin-1.170.tar.gz
cd webmin-1.170
sudo sh setup.sh
-------
In the install you will have several choices to make...
-------
Config file directory [/etc/webmin]:
# Leave as default, or change as you wish

Log file directory [/var/webmin]:
# Leave as default, or change as you wish

Full path to perl (default /usr/bin/perl):
# Leave as default, or change as you wish

Operating system:
#Enter '6'

Version:
#Enter '6'

Web server port (default 10000):
# This is where you can start to make webmin more secure then
# the standard install you get with apt-get, Synaptic, or RPM.
# Leave as default or change it to what ever port you want.

Login name (default admin):
# The first time I ran this I thought 'default admin' was 'root'...
# Nope.  It is 'admin', so you can leave it as that, or put in
# any name that you like.  I would recommend a name that is
# not installed on your system.

Login password:
# By creating the user above and giving it a password, you have
# now made it so you will not need to log into webmin with root.

Password again:
# Self explanatory

## If you did not install 'libnet-ssleay-perl' you will get the following message:
## 'The Perl SSLeay library is not installed. SSL not available.'
## You can continue with the install, but I would not recommend it.
## Install the file with Synaptic, and start the script over.
## You will then get the following:

Use SSL (y/n):
# Of course 'y'

Start Webmin at boot time (y/n):
#Once agian... 'y'

# At this point it is going to configure things, install things, and 
# create things... blah blah blah.
# It will then tell you that you can log in to [https://hostname:10000](https://hostname:10000)
# and to accept the certificate.

There you go... a more secure install of Webmin, and you will not need to go changing root issues on your system.  And even if you do... who cares.  Webmin won't.

-Readis

---

### Post by hndrcks on 2004-12-08
From webmin MAN page

to change root password in webmin use this included Perl script:

# /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>

---

### Post by jdong on 2004-12-08
Yeah, you can specify a separate root password for Webmin!

I'll be backporting the latest Webmin from Sid/Hoary to Warty within the next week or so.

---

### Post by wayover13 on 2004-12-08
I don't see why this is more secure: it's sure as heck not as easy as just assigning root a password before installing the regular webmin.  That's what I did and it works just fine.  Generating a package that integrates better with the Ubuntu way of sudo'ing all root-related tasks would be good though.  Webmin should take its password from the user's account rather than from root's somehow.  The more serious problem with Ubuntu/Webmin is that Ubuntu uses some non-standard way of dealing with LVM, and thus the Webmin module for LVM admin won't work.  A fix for that is what I really need.

---

### Post by TravisNewman on 2004-12-08
Why is it more secure? In the apt-getted one, If someone breaks into webmin they can then gain total control because they know your root password. In the installer script, you can set it up to use SSL. You can make it run on a non-standard port. You can make the name and password something that doesn't exist on your system anywhere (so if anyone breaks your account, they can't get into webmin).

---

### Post by Readis on 2004-12-08
[QUOTE=wayover13]I don't see why this is more secure: it's sure as heck not as easy as just assigning root a password before installing the regular webmin.  That's what I did and it works just fine.  Generating a package that integrates better with the Ubuntu way of sudo'ing all root-related tasks would be good though.[/QUOTE]

     One of my consulting jobs deals with network security.  Firewalls, IDS, internal and external audits... that sort of thing.  When an app like Webmin has the kind of power that it has, and is easy to use, you really need to make sure that it is locked down as much as possible.  I was always slightly nervous about Webmin only using root as a login.  When I would do an external scan on a client, if I saw webmin open on port 10000, and we always scaned for 10000 since it is the default port, we always knew that 99 out of 100 times root would be the login.  By knowing the user, you just cut your attack time WAY down!  At that point we could, *if we wanted*, brute force or low and slow the port, to see if we could get in.  Don't freak out.  We always had permission and a signed document that allowed this kind of work.  The smart ones would have webmin on a different port.  But most installed it from apt-get, RPM, or some other repository.  I didn't realize that the script existed until I started using Ubuntu.  
     Packages are great for 999 of 1000 apps.  It allows you to see how a program works, and see if it is something that you want to use.  But when it comes to security, I am not a huge fan of using them for this type of app.  If you want to run the package of Webmin, be my guest.  That is one of the things about Linux I love.  The ability to set things up the way you want.  Just remember it is not as secure as the install script.  
     I would also recommend changing the retrys and lockoput time period in the webmin options.  That's my 2 cents...

-Readis

---

### Post by jdong on 2004-12-13
Umm, webmin locks out the offender's IP after 3 incorrect logins... It'd take quite a number of IP's , and quite a bit of time to launch a brute force attack.

---

### Post by Readis on 2004-12-15
[QUOTE=jdong]Umm, webmin locks out the offender's IP after 3 incorrect logins... It'd take quite a number of IP's , and quite a bit of time to launch a brute force attack.[/QUOTE]

Actually, the default for Webmin is set at 5 attempts and then lockout for 60 seconds...  though I do change mine to 3 attempts and 180 seconds...

-Readis

---

### Post by jdong on 2004-12-15
either case, do the math.

How long will it take to permute an 8-character purely alphabetic password?

---

### Post by quackking on 2004-12-29
I've got 1.17.0 installed - but how can I get Ubuntu listed as a distribution in the Webmin Config page? If I configure the system as Debian 3.1 it does not really work (or there are some oddities.) Is there some config file I can download to make Ubuntu appear in the drop-down list of distros?

Also, has anybody Ubuntu-ported the Log Viewer module which comes with Mandrake? I have gotten used to it - but it seems the Russian web page which looks to be the source for the module is of the air.

---

### Post by zenwhen on 2004-12-29
I am getting ready to set this up on my Ubuntu server. It should be interesting to be able to mess with it from my web browser.

---

### Post by zenwhen on 2004-12-29
Set it up with this guide and only allowed my local network to access it. Thanks a lot. I was thinking about setting this up just this morning.

---

### Post by wayover13 on 2004-12-29
[QUOTE=Readis]Packages are great for 999 of 1000 apps.  It allows you to see how a program works, and see if it is something that you want to use.  But when it comes to security, I am not a huge fan of using them for this type of app.  If you want to run the package of Webmin, be my guest.  That is one of the things about Linux I love.  The ability to set things up the way you want.  Just remember it is not as secure as the install script.  
     I would also recommend changing the retrys and lockoput time period in the webmin options.  That's my 2 cents...[/QUOTE]

I guess I wasn't thinking that anyone would have webmin running on a system that was on the WAN/internet. I was presuming that any system it would be installed to would be behind a firewall. But I'm a personal computer user, so my assumptions are going to be different than someone who needs to admin web servers and such. Longer lockouts and extra passwords are just going to be a hassle for me: my firewall blocks all port 10000 (and just about every other port) traffic anyway, so only someone on this side of my firewall (i.e., inside my apartment) is going to be able to access webmin on my system. My response about not seeing how it's more secure--or maybe more hassle than it's worth--was based on assumptions about computer use like mine. For other situations, your method probably makes alot of sense, though.

Thanks, James

---

### Post by peekj on 2004-12-31
Just an FYI, I had to run setup.sh from a root terminal to make this work.
Trying to use "sudo setup.sh" did not ask me any questions during the installation other than the installation directory...

---

### Post by britishtrident on 2005-01-02
[QUOTE=panickedthumb]Why is it more secure? In the apt-getted one, If someone breaks into webmin they can then gain total control because they know your root password. In the installer script, you can set it up to use SSL. You can make it run on a non-standard port. You can make the name and password something that doesn't exist on your system anywhere (so if anyone breaks your account, they can't get into webmin).[/QUOTE]

The really important security tweak with webmin is to restrict access by using its built in  IP address filter  or if remote access is not required   to 127.0.0.1 only. Moving the port will help a little but is no defense  against any serious port scan.  

Like wise changing the default user from admin to something more complex and obscure will help and doing the same with the password  will help but is no denfense against the serious hacker  --- the internet is loaded with really powerful hacking tools.

Of course it goes without saying no to use the same password on Webmin as your root password and to make sure your router password and usr name are not the default ones.

---

### Post by danjmw on 2005-05-26
Readis' original instructions are excellent and his advise is very sound, from an IT Security perspective.  I just installed Webmin 1.200 from the package available from [www.webmin.com](www.webmin.com) (webmin-1.200.tar.gz) and it went smooth as could be.  The heads-up to load the SSL package libnet-ssleay-perl before installing Webmin also saved a lot of time and possible frustration.  Whether installing the app on a laptop or server its always a good idea to change up the port the service is listening on and using SSL whenever possible.  In past installations of Webmin I have used the root account for administration but the option available through the package installation is brilliant.

Thanks Readis, very helpful.

Dan

---

### Post by ensenadaubuntulover on 2005-05-28
[QUOTE=hndrcks]From webmin MAN page

to change root password in webmin use this included Perl script:

# /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>[/QUOTE]
 You are right!
UBUNTU IS DIFFERENT

---

### Post by Ubuntu Warrior on 2005-06-13
Having used apt to download and install webmin I would advise against this as the current Ubuntu version is extremely out of date! ... or am I missing something???

One of the major hassles with deploying Linux systems is the clumsy command-line interface without any really intuitive management tools. Webmin seems to be closing this gap but remains a stumbling block due to the lack of current ports.

Ubuntu is seen as a desktop Linux solution but I have many Ubuntu servers now deployed in our production environment hosting critical services like web, caching/proxying, dns, dhcp, etc. Such half-hearted support for a product like Webmin just seems to enforce the desktop view.

When are we going to have better support for Webmin?

---

### Post by Screwball on 2005-07-03
I have just attempted to install Webmin-1.210 following the instructions at the top of this thread. Everything **except** the "start at boot time" appeared to work correctly. Sadly, I received the following error:-
```
Failed to open /etc/rc.d/init.d/webmin :  No such file or directory
```This is understandable, as the startup scripts are in /etc/rc<runlevel>.d/S<2 digit sequence?>whatever (these are symlinks to "../init.d/whatever).  Note that I was **not** presented with the "operating system" or "version" prompts - all other prompts appeared and were allowed to retain their default settings.

Could anyone advise me on how to get webmin started at boot time please. ](*,)

---

### Post by isaiah55 on 2005-07-11
One thing I would recommend is that you don't use the latest version (1.210) as it automatically sets the Operating System for you (Generic Linux) and as such nothing works without altering the configuration settings.
I installed v1.200 which still allows you to choose the OS.

---

### Post by chill on 2005-07-12
maybe you are right. I installed fresh ubuntu server and logged in and run the commands:

[b]sudo apt-get update
sudo apt-get install libnet-ssleay-perl
sudo apt-get install samba
sudo apt-get install smbfs
cd /usr/local
sudo mkdir webmin
cd webmin
sudo wget [http://switch.dl.sourceforge.net/sourceforge/webadmin/webmin-1.210.tar.gz](http://switch.dl.sourceforge.net/sourceforge/webadmin/webmin-1.210.tar.gz)
sudo tar xzvf webmin-1.210.tar.gz
cd webmin-1.210
sudo sh setup.sh
[COLOR=DimGray]Config file directory [/etc/webmin]:[/COLOR] <enter> [/b]*(default)*[b]
[COLOR=DimGray]Log file directory [/var/webmin]:[/COLOR] <enter> [/b]*(default)*[b]
[COLOR=DimGray]Full path to perl (default /usr/bin/perl): [/COLOR]<enter> [/b]*(default)*
*... then it never asked no operating system info ...*[b]
[COLOR=DimGray]Web server port (default 10000):[/COLOR] 1024 [/b]*(a free port I quess)*[b]
[COLOR=DimGray]Login name (default admin):[/COLOR] john [/b]*(u name it)*[b]
[COLOR=DimGray]Login password:[/COLOR] Doe1239 [/b]*(as you wish)*[b]
[COLOR=DimGray]Password again:[/COLOR] Doe1239 [/b]*(again)*[b]
[COLOR=DimGray]Use SSL (y/n):[/COLOR] y
[COLOR=DimGray]Start Webmin at boot time (y/n):[/COLOR] y[/b]

I jumped to another PC and accessed the webmin from: [https://192.168.1.234:1024/](https://192.168.1.234:1024/) and frankly - it almost worked.

**1.** when I clicked samba server icon it gave me an error message ... something about not finding the samba conf files or paths. looks like samba was not where webmin expected it to be. but webmin had an option to fix the paths. next problem, how should I know what are the right locations. I tried to **find** the files and corrected the conf and I somewhat almost got the samba to communicate with webmin (vice versa). but I was not able to restart the samba server via webmin. it gave me an error that I do not remember right now. I quess I did not put all the paths as they should have been.

**2.** second problem. when I restarted the server - I was no longer able to access the webmin from the very same url. the error message said someting like "Access denied" or "Forbidden"... something like that. I suppose the webmin did not start along with server. It simply does not listen the port anymore?

Since installing the server went pretty fast. I thought I made a mistake somehwere and I did it all over again. But the results were same.

**Am I the only one with this sort of problem? Can anybody tell me, what went wrong? Or should I stick to older version of webmin - although, it does not feel like a right solution. Or should I try SWAT for samba and WEBMIN for other tasks?**

Thank you,

---

### Post by gkozlyk on 2005-07-28
I have successfully put in Webmin on my Hoary Ubuntu Box.  I have updated all the directory info in the Windows File Sharing and seems to be running fine.  Now on the Windows box i can see my ubuntu box however when i doubleclick it, i can't log into it.   I can ping the ubuntu boxes IP address, i just can't get in.  I am running a laptop with XP which i want to access the ubuntu tower.

Is there something i am missing?

---

### Post by Maxplayer14 on 2005-07-29
[QUOTE=chill]maybe you are right. I installed fresh ubuntu server and logged in and run the commands:

[b]sudo apt-get update
sudo apt-get install libnet-ssleay-perl
sudo apt-get install samba
sudo apt-get install smbfs
cd /usr/local
sudo mkdir webmin
cd webmin
sudo wget [http://switch.dl.sourceforge.net/sourceforge/webadmin/webmin-1.210.tar.gz](http://switch.dl.sourceforge.net/sourceforge/webadmin/webmin-1.210.tar.gz)
sudo tar xzvf webmin-1.210.tar.gz
cd webmin-1.210
sudo sh setup.sh
[COLOR=DimGray]Config file directory [/etc/webmin]:[/COLOR] <enter> [/b]*(default)*[b]
[COLOR=DimGray]Log file directory [/var/webmin]:[/COLOR] <enter> [/b]*(default)*[b]
[COLOR=DimGray]Full path to perl (default /usr/bin/perl): [/COLOR]<enter> [/b]*(default)*
*... then it never asked no operating system info ...*[b]
[COLOR=DimGray]Web server port (default 10000):[/COLOR] 1024 [/b]*(a free port I quess)*[b]
[COLOR=DimGray]Login name (default admin):[/COLOR] john [/b]*(u name it)*[b]
[COLOR=DimGray]Login password:[/COLOR] Doe1239 [/b]*(as you wish)*[b]
[COLOR=DimGray]Password again:[/COLOR] Doe1239 [/b]*(again)*[b]
[COLOR=DimGray]Use SSL (y/n):[/COLOR] y
[COLOR=DimGray]Start Webmin at boot time (y/n):[/COLOR] y[/b]

I jumped to another PC and accessed the webmin from: [https://192.168.1.234:1024/](https://192.168.1.234:1024/) and frankly - it almost worked.

**1.** when I clicked samba server icon it gave me an error message ... something about not finding the samba conf files or paths. looks like samba was not where webmin expected it to be. but webmin had an option to fix the paths. next problem, how should I know what are the right locations. I tried to **find** the files and corrected the conf and I somewhat almost got the samba to communicate with webmin (vice versa). but I was not able to restart the samba server via webmin. it gave me an error that I do not remember right now. I quess I did not put all the paths as they should have been.

**2.** second problem. when I restarted the server - I was no longer able to access the webmin from the very same url. the error message said someting like "Access denied" or "Forbidden"... something like that. I suppose the webmin did not start along with server. It simply does not listen the port anymore?

Since installing the server went pretty fast. I thought I made a mistake somehwere and I did it all over again. But the results were same.

**Am I the only one with this sort of problem? Can anybody tell me, what went wrong? Or should I stick to older version of webmin - although, it does not feel like a right solution. Or should I try SWAT for samba and WEBMIN for other tasks?**

Thank you,[/QUOTE]

Nope this same thing happened to me.  5.04.  I get this when I try to start/restart it.

```
root@jdog:/ # /etc/init.d/webmin start
Starting webmin: webmin.
root@jdog:/ # /etc/init.d/webmin restart
Restarting webmin: start-stop-daemon: warning: failed to kill 10324: No such process
webmin.
root@jdog:/ #
```

Anyway to fix this?

---

### Post by Maxplayer14 on 2005-08-01
Does anyone have a working Webmin?  I have tried everything and it still doesn't start after reboot.

---

### Post by ameerirshad on 2005-08-04
Hi

I have webmin installed, with support for apache, bind, fetchmail, mysql, postgresql, procmail and spamassasin (well don't ask me why I have some duplicate apss running!)..... as I used the webmin feature to upgrade to the latest version, I can't open webmin anymore, but neither can I remove it. As in synaptic, nor ap-get can remove it, both giving me the following error (from Synaptic) E: webmin-apache: subprocess pre-removal script returned error exit status 2

E: webmin-bind:  subprocess pre-removal script returned error exit status 2
E: webmin-core:  subprocess pre-removal script returned error exit status 2
E: webmin-dhcpd:  subprocess pre-removal script returned error exit status 2
E: webmin-fetchmail:  subprocess pre-removal script returned error exit status 2
E: webmin-inetd:  subprocess pre-removal script returned error exit status 2
E: webmin-mysql:  subprocess pre-removal script returned error exit status 2
E: webmin-postgresql:  subprocess pre-removal script returned error exit status 2
E: webmin-procmail:  subprocess pre-removal script returned error exit status 2
E: webmin-software:  subprocess pre-removal script returned error exit status 2
E: webmin-spamassassin:  subprocess pre-removal script returned error exit status 2

Does anyone knows how I can get rid of these aps? I mean, everytime I install, upgrade or otherwise alter some program using apt-get or synaptic, it tells me I have 11 broken links, but refuses to repair or remove them!

thnx alot 

newbee to Linux

---

### Post by ninotob on 2006-01-01
[QUOTE=hndrcks]From webmin MAN page

to change root password in webmin use this included Perl script:

# /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>[/QUOTE]

I see this suggestion everywhere.  Except it isn't working for me.  I run that comman, restart webmin, heck -- even restart apache, nothing.  Right now all I want to do is figure out how to make it not timeout after three failed login attemps.  

Anyway, what is the magic package I have to install for this script to work?  I have it, and it runs, and it changes the entry in /etc/webmin/miniserv.users -- but I still get failure at my login prompt.

edit: using breezy and I really don't want to enable root.

---

### Post by TomH on 2006-02-06
Does anyone know the correct location of the samba stuff for webmin? I tried to find them but with little luck :( As follows:

Location of the Samba configuration file   
Location of the Samba password file  None       
Full path to smbstatus   
Full path to smbpasswd   
Full path to smbd   
Full path to nmbd   
Full path to swat  None       
Full path to smbgroupedit  None       
Full path to pdbedit  None       
Full path to net command  None       
Command to start Samba servers  Automatic       
Command to stop Samba servers  Just kill processes      


Would be greatly apreciated

Tom

---

### Post by raru on 2006-02-07
Hi List,
 I have had problem to run MySQL Database Server through Webmin, I havee MySQL version 4.0.24. If anybody able to run mysql server through webmin successfully please help me to configure it on webmin
Following are my configuration

This in on Webmin : MySQL server configuration which I have done

System configuration
------------------------
Path to mysqlshow command          /usr/bin/mysqlshow
Path to mysqladmin command        /usr/sbin/mysqld	
Path to mysql command 	               /usr/bin/mysql
Path to mysqldump command 	  /usr/bin/mysqldump
Path to mysqlimport command 	  /usr/bin/mysqlimport
Command to start MySQL server 	                /etc/init.d/mysql start
Command to stop MySQL server 	                 Automatic   
Path to MySQL shared libraries directory 	 /usr/lib  
Path to MySQL databases directory 	         /var/lib/mysql 
MySQL host to connect to 	                      localhost   
MySQL port to connect to 	                       3306  
MySQL socket file 	                                    var/run/mysqld/mysqld.sock
MySQL configuration file                                /etc/mysql/my.cnf


----------------------------
My problem to
Command to start MySQL server 	                /etc/init.d/mysql start
that is work on xTerm but not work on Webmin


After Saving these configuration on Webmin to respond like

MySQL is not running on your system - database list could not be retrieved.

Click this button to start the MySQL database server on your system with the command /etc/init.d/mysql start. This Webmin module cannot administer the database until it is started.

-------------------------
That is the problem to run MySQL server through webmin

but through xterm it work, through  command /etc/init.d/mysql start

help me.

---

### Post by Thulemanden on 2006-02-14
With ver 1.260 Webmin no longer stops to ask for user and password during installation, so it looks grim using webmin in Ubuntu. However Sourceforge holds the older versions and I'll givet it a try.

Nope .170 doesn't stop to ask for user/password during installl.

---

### Post by Spudgun on 2006-02-24
[QUOTE=Thulemanden]With ver 1.260 Webmin no longer stops to ask for user and password during installation, so it looks grim using webmin in Ubuntu. However Sourceforge holds the older versions and I'll givet it a try.

Nope .170 doesn't stop to ask for user/password during installl.[/QUOTE]

Install version 1.200, and choose OS 6, and then version 6. After it's installed, you can upgrade to the newest version from within Webmin (Webmin --> Webmin Configuration --> Upgrade Webmin).

Good luck!

---

### Post by alancw on 2007-05-18
For some reason, doing the install as above introduced garbled control characters into the config file. Hence I too was unable to start webmin following a reboot. 

A quick change to the file and I can access webmin from another machine. The file is /etc/webmin/miniserv.conf 

So back it up first, then edit it (say with nano or whatever you use)
sudo nano /etc/webmin/miniserv.conf

remove the control characters after port: so that your port number is shown properly. Save the file, exit nano

Then to start it webmin again:
sudo /etc/webmin/start  (or 'stop' first  if it's already running)

---

### Post by elect on 2007-12-05
Is it possibile to use amule?

---

### Post by juky on 2008-05-31
Hi all,

I have followed this guide: [http://zebardast.wordpress.com/2008/01/22/webmin-installing-on-ubuntu-gutsy-gibbon-710/](http://zebardast.wordpress.com/2008/01/22/webmin-installing-on-ubuntu-gutsy-gibbon-710/)

and it worked.

Hope it helps.

Cheers,
juky

---

### Post by ShizzlePDX503 on 2009-10-16
I just installed webmin 1.490 via the .deb file that is offered on the webmin website. It successfully installed with no problems and now when I go to [https://localhost:10000](https://localhost:10000) I get this error:

```
localhost:10000 uses an invalid security certificate.

The certificate is not trusted because it is self signed.
The certificate is only valid for <a id="cert_domain_link" title="*">(null)</a>

(Error code: sec_error_untrusted_issuer)
```

I tried to follow this fix: 

To request a certificate, follow these steps :
 
[LIST]
[*]Run the command openssl genrsa -out key.pem 1024 . This will create the     file key.pem which is your private key.
[*]Run the command openssl req -new -key key.pem -out req.pem . When     it asks for the common name, be sure to enter the full hostname of your     server as used in the URL, like [www.yourserver.com](www.yourserver.com). This will create the     file req.pem, which is the certificate signing request (CSR)
[*]Send the CSR to your certificate authority by whatever method they use.     They should send you back a file that starts with     -----BEGIN CERTIFICATE----- which can be put in the file     cert.pem.
[*]Combine the private key and certificate with the command     cat key.pem cert.pem >/etc/webmin/miniserv.pem.
[*]Re-start webmin (making sure it is in SSL mode) to use the new key.
[/LIST]
I am not sure how I would send the CSR to a certificate authority. Does anyone know how I go about doing this?

BTW I got those instructions on the FAQ section on their website [http://www.webmin.com/faq.html](http://www.webmin.com/faq.html)

TIA

---

### Post by ShizzlePDX503 on 2009-10-16
Nevermind, it cost a lot of money to buy a certificate... not that important for me to spend that kind of money.

---

