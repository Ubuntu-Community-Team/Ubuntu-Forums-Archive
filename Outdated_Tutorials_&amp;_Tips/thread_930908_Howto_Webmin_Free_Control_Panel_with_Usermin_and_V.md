---
title: "Howto: Webmin Free Control Panel with Usermin and Virtualmin on Ubuntu 8.04"
date: 2008-09-26
forum: Outdated Tutorials &amp; Tips
---

### Post by dejitarob on 2008-09-26
[Webmin]("http://www.webmin.com") is a free and open source web-based control panel for Linux system administration. It is very feature-rich and simple to use, a worthy contender with cPanel and Plesk imo. Webmin provides .deb files to make installation easier, however there is some configuration necessary to get it working with Ubuntu 8.04 that took me a little bit to figure out. Webmin goes well with an [OpenVZ]("http://openvz.org") VPS (see [my howto]("http://ubuntuforums.org/showthread.php?t=929106")). See [http://www.webmin.com](http://www.webmin.com) for more info.

Virtualmin is a Webmin module (also comes as a standalone package) for managing multiple domains with a single host. Once installed it creates another tab named Virtualmin when logged into Webmin. Usermin is another useful Webmin module that provides more automation of user administration.

I used to set it up manually but now recommend just using Virtualmin's install script. It supports Ubuntu 8.04 and will automatically install the necessary packages (including Webmin and Usermin) and configuration. It is available at [http://webmin.com/vinstall.html](http://webmin.com/vinstall.html)

Make sure you have the [universe repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu") enabled before installing. If you run into problems check the log at /root/virtualmin-install.log

Check out [http://www.virtualmin.com/documentation/id,virtualmin_on_low_memory_systems](http://www.virtualmin.com/documentation/id,virtualmin_on_low_memory_systems) for ways to save memory with Virtualmin. There are some good specifics in the sample config at the end too.

---

### Post by cmileto on 2008-09-30
ty!!

---

### Post by dileepa on 2008-11-10
Excellent howto , how ever when I try to create a new domain using virtualmin I get this

**Failed to create virtual server : Cannot write to directory /etc/postfix/virtual**


and the account creation progress is like this

Creating administration group test.mydomain.com ..
.. done Creating administration user test ..
.. done
 Creating aliases for administration user ..
.. aliases failed : Cannot write to directory /etc/postfix/virtual at ../web-lib-funcs.pl line 1010. 
 Adding administration user to groups ..
.. done
 Creating home directory ..
.. done
 Creating mailbox for administration user ..
.. done
 Adding to email domains list ..
.. Mail for domain failed! : Cannot write to directory /etc/postfix/virtual at ../web-lib-funcs.pl line 1010. 
 Adding new virtual website ..
.. done
 Adding Apache user www-data to server's group ..
.. done
 Setting up scheduled Webalizer reporting ..
.. Webalizer reporting failed! : Cannot write to directory /etc/postfix/virtual at ../web-lib-funcs.pl line 1010. 
 Creating SSL certificate and private key ..
.. done
 Adding new SSL virtual website ..
.. done
 Setting up log file rotation ..
.. Log file rotation failed! : .. the log file /home/test/logs/access_log is already being rotated at ../web-lib-funcs.pl line 1010. 
 Creating MySQL login ..
.. done
 Creating MySQL database test_mydomain_com ..
.. done
 Creating FTP virtual server ..
.. done
 Adding ProFTPd user ftp to server's group ..
.. done
 Creating Webmin user ..
.. done
 Adding virtual IP interface for 192.168.103.16 ..


Can you give any idea why this happens ?

Many Thanks , 
D

---

### Post by dejitarob on 2008-11-10
> **dileepa said:**
> Excellent howto , how ever when I try to create a new domain using virtualmin I get this

**Failed to create virtual server : Cannot write to directory /etc/postfix/virtual**
What is the output of ```
ls -al /etc/postfix | grep virtual
```

Mine is ```
-rw-r--r--  1 root root  3328 Nov  7 16:27 virtual
```

If your's is different, do
```
chmod 644 /etc/postfix/virtual
chown root:root /etc/postfix/virtual
```

---

### Post by dejitarob on 2008-12-04
I now recommend just using Webmin/Virtualmin's install script. It supports Ubuntu 8.04 (possibly 8.10 too) and will automatically install the necessary packages and make configuration changes I outline below. It is available at [http://webmin.com/vinstall.html](http://webmin.com/vinstall.html)

---

### Post by brack on 2009-03-06
I'm trying to use the instal.sh script from virtualmin site and first I tried it with apache2 already working and it gives errors during installation, then I decided to try on clean machine, and script worked longer but still I get ```
Error: An error was detected in the new Cron configuration : <pre></pre> <pre>0,5,10,15,20,25,30,35,40,45,50,55 * * * * /etc/webmin/status/monitor.pl
```and after that whenever I try to ran apt-get I see following respond: ```
Errors were encountered while processing:
 virtualmin-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I dont have an idea what else to do.

---

### Post by dejitarob on 2009-03-06
What version of Ubuntu are you running? 

What is your output of 'crontab -l'?

Can you attach a copy of /var/log/apt/term.log ?

Also, try 'sudo dpkg --configure -a'

---

### Post by infallible on 2009-03-07
The install.sh scripin the linkyou provided does not work with my install; it fails when it discovers webmin is not in the repositoried for intrepid. However, the .deb package [here]("http://superb-east.dl.sourceforge.net/sourceforge/webadmin/webmin_1.450_all.deb") installed with [these instructions]("http://webmin.com/deb.html") worked out for me.

---

### Post by dejitarob on 2009-03-07
> **infallible said:**
> The install.sh scripin the linkyou provided does not work with my install; it fails when it discovers webmin is not in the repositoried for intrepid.Yes I believe the script has a warning when you run it that it's only for 8.04 unfortunately. When installing with the .debs I needed some manual configuration, see my first post above.

---

### Post by binbash on 2009-03-08
Nice tutorial thanks

---

### Post by brack on 2009-03-09
> **dejitarob said:**
> What version of Ubuntu are you running? 

What is your output of 'crontab -l'?

Can you attach a copy of /var/log/apt/term.log ?

Also, try 'sudo dpkg --configure -a'

I run ubuntu 8.04 server, 'crontab -l' returns 'bash: crontab: command not found' and lastly 'sudo dpkg --configure -a' doesnt do anything

After following this tutorial "http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p6" I was able to setup server manually, then disabled suexec and set the document folder to /home/user/public_html but keep getting " You don't have permission to access / on this server." now.

---

### Post by brack on 2009-03-09
new try of installation of virtualmin returns the same errors:```
Displaying the last 15 lines of /root/virtualmin-install.log to help troubleshoot this problem:
Configuring resolv.conf to use local DNS server
Enabling status monitoring
Error: An error was detected in the new Cron configuration : <pre></pre> <pre>0,5,10,15,20,25,30,35,40,45,50,55 * * * * /etc/webmin/status/monitor.pl
</pre>
Error
-----
An error was detected in the new Cron configuration : <pre></pre> <pre>0,5,10,15,20,25,30,35,40,45,50,55 * * * * /etc/webmin/status/monitor.pl
</pre>
-----
dpkg: error processing virtualmin-base (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 virtualmin-base

```
The virtualmin interface starts on port 10000 and checking configuration returns this:```
The status of your system is being checked to ensure that all enabled features are available, that the mail server is properly configured, and that quotas are active ..

      BIND DNS server is installed, and the system is configured to use it.
```
But the very next time I login there I requires me to check configurations. Basically the only thing that I can do is to check configurations. 
'sudo dpkg --configure -a' now goes through setting up virtualmin-base but hangs on the line 'Configuring resolv.conf to use local DNS server' Dont know how to skip this or something.

---

### Post by brack on 2009-03-10
Ok, even I get all errors above I could manage to use webmin and setup virtual server through Webmin, (not through Virtualmin) and looks like everything is working. there where some permission problems but I fixed everything manually. specially this is the only xen machine that I had problems to install stuff via install.sh script, other machines setup perfectly fine, even on the same pc. Dont have much time to sort this problem, will do it next month.

---

### Post by dejitarob on 2009-03-11
I honestly don't know what to say. If you don't have crontab there might be something really messed up with your Ubuntu install. Do you get these errors on a clean install? I've used the script about 20 times for installing OpenVZ VPSs at my work and never had a problem.

---

### Post by brack on 2009-03-13
Ok, the problem is solved. When I was creating this xen machine I used buggy script - it didnt make swap so there was only virtual memory. Now I fixed the script, and I have swap and virtualmin installed without single problem.

---

### Post by Radio91 on 2009-06-14
If you are using the installation script on a VPS with a fresh install of Ubuntu 8.x do you still have to manually take steps to secure the server or does the installation script handle this?

---

### Post by dejitarob on 2009-06-14
> **Radio91 said:**
> If you are using the installation script on a VPS with a fresh install of Ubuntu 8.x do you still have to manually take steps to secure the server or does the installation script handle this?
Good question. I think it depends on how secure you want your server and what you are using your server for. The Virtualmin installer script does a pretty good job of providing a base level of security I believe--it won't leave your server as an open relay for example. But it's not going to setup a firewall for you, or SSH restrictions, suphp, etc.

---

### Post by Radio91 on 2009-06-15
cheers

Can you point to a good step by step Howto tutorial for setting up a decent level of security in ubuntu 8?

---

### Post by SwellJoe on 2009-06-15
"setting up a decent level of security in ubuntu 8"
 
 It should have a "decent level of security" out of the box.  ;-)
 
 Firewalls have limited utility in a virtual hosting environment...the services you want to use need to be available to everyone, so you can't firewall them.  Services that you don't need shouldn't even be running, so firewalling the port is meaningless.  You can make use of stateful firewall rules to do clever things like block large numbers of new connections on important ports like ssh (the connection will be "ESTABLISHED" or "RELATED" once a session is started with a user, so lot of new connections is suspicious and might indicate a brute force attack, for example).  But, this isn't necessarily the most important use of your time when it comes to security.
 
 The most important security concepts are very simple, but a lot of people get them wrong:
 
 1. Keep your system up to date.  In a system with many services running, there will occasionally be security issues discovered.  So, you need to update immediately when fixes for security issues arrive.  This is the leading attack vector used against servers.  You cannot run out of date software on your system.  Ubuntu provides apt-get, and has a good security response history, so as long as you stay on top of Ubuntu-provided updates (and you're taking advantage of the Virtualmin.com apt-get repository for those packages), you'll be way ahead of the game on security.
 
 2. Strong passwords.  Never use weak passwords, even for low-powered accounts.  A strong password is 8+ characters in length, has numbers and letters and optional punctuation and is not based on dictionary words..  Gaining low-level shell access is the first step in an escalation attack, and so even a simple account can be dangerous (particularly if you forget to update your system, and a new local exploit is discovered).
 
 3. Don't run unnecessary services.  Every piece of software running on your system is a potential attack vector.  The less you run, the safer you are.  So, figure out what services you need, and make sure any you don't have been shut down.
 
 There's all sorts of snake oil security advice out there, but a lot of it is just distraction from the important stuff.  If you do those three things...*then *you can look around for other hardening advice.  But don't get distracted from the core security principles.
 
 For Virtualmin specific advice, if you'll be sharing your box with other users, you'll want to switch to running all scripts under suexec.  This is the default for regular CGI scripts in Virtualmin GPL, but PHP still runs under mod_php (which means as the Apache user), so switching to suexec+FastCGI is recommended.  If you don't share your box, or only with trusted users, then this isn't a very big deal.  suexec makes web applications run as the user that owns the virtual host in which they run, which prevents them from snooping on other virtual hosts data, among other things.
 
 We've covered this process a few times in our forums at Virtualmin.com, and this is the mostly definitive thread with a HOWTO:
 
 [http://www.virtualmin.com/node/8462](http://www.virtualmin.com/node/8462)

---

### Post by dejitarob on 2009-06-15
Thanks for the informative post Joe. The exploits I've seen and fixed in my limited experience as a sysadmin were nearly all due to #1 and #2. Then there's always the problem with end users getting their passwords stolen due to trojans on their own boxes but not much you can do about that besides having some damage control in place, which you also outline.

---

### Post by Radio91 on 2009-06-15
Awesome joe thanks a lot! 

Does the virtualmin script update ubuntu to the latest version or do you have to do that yourself?

---

### Post by dejitarob on 2009-06-15
It definitely doesn't change your Ubuntu release (which isn't necessary to have the latest security updates) and I don't believe it updates your packages either. But the latter is real easy to do with a simple ```
apt-get update; apt-get upgrade
```

---

### Post by Radio91 on 2009-06-15
Yeah thanks I wasn't sure if those commands would update to an entirely different version release or just update to latest version of my current release.

---

### Post by dejitarob on 2009-06-15
Yea just updates currently installed packages. To go to the next release: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Radio91 on 2009-06-15
Dam it the install script failed 

Reading package lists...
Building dependency tree...
Reading state information...

FATAL - Fatal Error Occurred: Something went wrong during installation: 0
FATAL - Cannot continue installation.
FATAL - Attempting to remove virtualmin repository configuration, so the installation can be
FATAL - re-attempted after any problems have been resolved.
FATAL - Removing temporary directory and files.
FATAL - If you are unsure of what went wrong, you may wish to review the log
FATAL - in /root/virtualmin-install.log


Just trying to figure out how to open this log now

---

### Post by dejitarob on 2009-06-15
nano /root/virtualmin-install.log
or 
less /root/virtualmin-install.log

---

### Post by Radio91 on 2009-06-15
the log file tells me nothing of use anyway!


INFO - 2009-06-15 23:52:14 - Removing Debian apache packages...
DEBUG - 2009-06-15 23:52:14 - Reading
INFO - 2009-06-15 23:52:15 - Installing dependencies using command: /usr/bin/apt-get --config-file apt.conf.noninteractive -y --force-yes install postfix postfix-pcre webmin usermin ruby libapache2-mod-ruby libxml-simple-perl libcrypt-ssleay-perl unzip zip quota
Reading package lists...
Building dependency tree...
Reading state information...
FATAL - 2009-06-15 23:52:16 - Fatal Error Occurred: Something went wrong during installation: 0
FATAL - 2009-06-15 23:52:16 - Cannot continue installation.
FATAL - 2009-06-15 23:52:16 - Attempting to remove virtualmin repository configuration, so the installation can be
FATAL - 2009-06-15 23:52:16 - re-attempted after any problems have been resolved.
FATAL - 2009-06-15 23:52:16 - Removing temporary directory and files.
FATAL - 2009-06-15 23:52:16 - If you are unsure of what went wrong, you may wish to review the log
FATAL - 2009-06-15 23:52:16 - in /root/virtualmin-install.log

---

### Post by dejitarob on 2009-06-15
Hmm, is there anything above that first line you posted "Removing Debian apache packages?" Every now and then I run into a snag having to do with a package. It will usually say somewhere in the log what package it is and just requires it to be installed manually. At least this is my experience.

---

### Post by Radio91 on 2009-06-15
ahh i found something:

INFO - Removing Debian standard Webmin package, if they exist (because they're b                        roken)...
INFO - Removing Debian apache packages...
INFO - Installing dependencies using command: /usr/bin/apt-get --config-file apt                        .conf.noninteractive -y --force-yes install postfix postfix-pcre webmin usermin                         ruby libapache2-mod-ruby libxml-simple-perl libcrypt-ssleay-perl unzip zip quota
...in progress, please wait...
.E: Couldn't find package libapache2-mod-ruby

/usr/bin/apt-get --config-file apt.conf.noninteractive -y --force-yes install po                        stfix postfix-pcre webmin usermin ruby libapache2-mod-ruby libxml-simple-perl li                        bcrypt-ssleay-perl unzip zip quota failed.  Error (if any): 0

---

### Post by dejitarob on 2009-06-15
Yup! That's really weird. That same package sometimes gives me trouble too. It seems random and I can't reproduce it (I'm always installing on OpenVZ VPSs running Ubuntu 8.04 with all the standard repositories enabled). Maybe it is a bug though if others get it too. What release of Ubuntu are you running?

You can fix it with:
```
apt-get install libapache2-mod-ruby
``` and then run the script again.

---

### Post by Radio91 on 2009-06-15
its 8.04 updated with the commands you gave me above

---

### Post by Radio91 on 2009-06-15
it cant find it apparently:

apt-get install libapache2-mod-ruby
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libapache2-mod-ruby

---

### Post by Radio91 on 2009-06-15
at a loss with what to do now

---

### Post by Radio91 on 2009-06-15
Ok after a bit of digging and asking on the virtualmin forums I found the problem.

The Version of ubuntu that was installed on my VPS never had the universe repository added to the /etc/apt/sources.list.

I added the following lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

and then ran apt-get update

The install script now seems to work. 

Hope some other newbi find this useful ;)

---

### Post by Radio91 on 2009-06-16
Are there any step by step howto's on how to setup DNS servers in Virtualmin Im a little confused

---

### Post by dejitarob on 2009-06-16
What are you trying to do, run your own nameserver? From what I understand you can disable BIND unless you really need your own nameserver.

---

### Post by Radio91 on 2009-06-16
well iv setup my VPS with virtualmin and its all running sweet but I cant use the providers nameservers so I assume I will have to setup my own nameserver? Id rather avoid this if possible and use somthing like godaddys free dns service but Im not sure how this will work with the virtual servers and their associated domain names ect..

---

### Post by dejitarob on 2009-06-16
Check with your domain registrar. They should have some kind of DNS interface you can use with their nameservers to change the @, www, and MX records of your domain to the IP address of your VPS. If not, I'd transfer to a registrar that knows what they are doing hehe. I work for [http://4domains.com](http://4domains.com) and we have a free DNS management interface, which is pretty standard among established registrars.

If you do actually want to run your own nameservers you will need two separate IPs and then register them. Your registrar will have to do this for you.

---

### Post by Radio91 on 2009-06-16
Well I can edit every aspect of the DNS at godaddy via total DNS control but how will the effect the running of virtualmin and setting up virtual servers for clients and mail accounts for them ect..?

---

### Post by dejitarob on 2009-06-16
You will have to do the same with their domains too. The other option is to run your own custom nameservers and have them set their domains to your custom nameserver.

---

### Post by Radio91 on 2009-06-16
Yeah id rather avoid using custom namesevers if possible and just disable bind saving ram.

---

### Post by dejitarob on 2009-06-16
Check out [http://www.virtualmin.com/documentation/id,virtualmin_on_low_memory_systems](http://www.virtualmin.com/documentation/id,virtualmin_on_low_memory_systems) for other ways to save memory. There are some good specifics in the sample config at the end too.

---

### Post by Radio91 on 2009-06-16
Iv got it resolving to my ip address but I cant get the mail servers to work at all.

---

### Post by dejitarob on 2009-06-18
Not sure what you exactly mean by that (sending, receiving, bounce backs, etc?) but does /var/log/mail.log give any clues?

---

### Post by Radio91 on 2009-06-21
I managed to get the Dns and nameservers set up OK but I have one final issue that I cant see to resolve.

In virtualmin system information ProFTPd FTP Server is not running, when I try to enable it I get the following error:

Failed to start service :

    * Starting ftp server proftpd
    * warning: unable to determine IP address of 'ns1.mydomain.com_'
    * error: no valid servers configured
    * Fatal: error processing configuration file '/etc/proftpd/proftpd.conf' ...fail!

I tired to edit the /etc/proftpd/proftpd.conf and remove the  _ from the end of ns1.mydomain.com but its not in that file.

There is no typos in /etc/hosts and /etc/hostname

/etc/hosts:

127.0.0.1        localhost.localdomain localhost
94.xx.xxx.xxx    ns1.mydomain.com ns1
94.xx.xxx.xxx    ns2.mydomain.com ns2

hostname is returing ns1.mydomain.com which is correct but

hostname -f is returning:
 
hostname: Unknown host   

Which makes no sense!

Any idea whats going on here?

---

### Post by Radio91 on 2009-06-24
anybody got any idea where this might be?

ns1.mydomain.com_

---

### Post by Francewhoa on 2009-06-30
Great post thanks dejitarob. 

@all: If you're are an absolute beginner I wrote a how-to handbook at [http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883) It covers installing Virtualmin, Webmin & Usermin on Ubuntu Server 8.04 LTS.

---

