---
title: "Howto: secure your sshd using DenyHosts"
date: 2006-09-09
forum: Outdated Tutorials &amp; Tips
---

### Post by TwoWordz on 2006-09-09
Hi everyone, 

I was browsing thru the forums and I noticed there was no howto explaining how to setup DenyHosts on ubuntu. I looked around and found a guide on [howtoforge.com]("http://www.howtoforge.com"). 

This guide is heavily based on [the one at howtoforge]("http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts"). I installed and configured the script on my freshly installed dapper without problems so nothing should be left out in this guide. 

*I would like to thank Falko Timme for his excellent howto. *

update: It seems that DenyHosts is now available in the repositories for Edgy and Feisty. (Thanks Jussi Kukkonen)

So, what is denyhost? Here is the description from the website:

> [I]DenyHosts is a script intended to be run by Linux system administrators to help thwart SSH server attacks (also known as dictionary based attacks and brute force attacks). 
If you've ever looked at your ssh log (/var/log/secure on Redhat, /var/log/auth.log on Mandrake, etc...) you may be alarmed to see how many hackers attempted to gain access to your server. Hopefully, none of them were successful (but then again, how would you know?). Wouldn't it be better to automatically prevent that attacker from continuing to gain entry into your system? 

DenyHosts attempts to address the above... and more[/I]  

The latest version of denyhost is 2.5 and needs python 2.4 to run:

```
sudo apt-get install python2.4
```

Then, we download DenyHosts from sourceforge:

```
wget http://prdownloads.sourceforge.net/denyhosts/DenyHosts-2.5.tar.gz?use_mirror=easynews
```

Extract it to your working directory:

```
tar xvzf DenyHosts-2.5.tar.gz
```

And install it :

```
cd DenyHosts-2.5
sudo python setup.py install
```

Now we need to configure it to work with our ubuntu install :

```
cd /usr/share/denyhosts
```

copy the sample configuration file:

```
sudo cp denyhosts.cfg-dist denyhosts.cfg
```

Some variables need to be set up before we can start denyhosts:

```
sudo nano denyhosts.cfg
```

```
SECURE_LOG = /var/log/auth.log
LOCK_FILE = /var/run/denyhosts.pid
```

And I use:

```
BLOCK_SERVICE = ALL
```
(if someone tries to bruteforce my ssh, I don&#8217;t see why I should let him connect to my other services, you can do what you want here)

*There are options to get notifications by mail when a host is added to the deny.host file. You can do it if you want but be prepared to receive a lot of mail from the daemon. First time I set it up, I had some hosts banned after just a couple of minutes! *

After that, we ne to setup the startup script for the daemon:

```
sudo cp daemon-control-dist daemon-control

sudo nano daemon-control
```

Here are the variables you need to change:

```
DENYHOSTS_BIN = "/usr/bin/denyhosts.py"
DENYHOSTS_LOCK = "/var/run/denyhosts.pid"
DENYHOSTS_CFG = "/usr/share/denyhosts/denyhosts.cfg"
```

Then we secure the file and make it executable:

```
sudo chown root daemon-control
sudo chmod 700 daemon-control
```

And finally, we make the script run at startup and we start the daemon:

```
cd /etc/init.d
sudo ln -s /usr/share/denyhosts/daemon-control denyhosts
sudo /etc/init.d/denyhosts start
update-rc.d denyhosts start 89 2 3 4 5 . stop 88 0 1 6 .

```

For added security, I would also recommend denying root logins  by editing the sshd_config file:

```
sudo nano /etc/ssh/sshd_config

PermitRootLogin no
```

I hope this guide helps you secure your box from uninvited guests. 

Feel free to tell me If you have any comments or if you see some typos.

---

### Post by TongueFish on 2006-09-14
you forgot to run update-rc.d to make the daemon run at boot.

this works ok for my system:
update-rc.d denyhosts start 89 2 3 4 5 . stop 88 0 1 6 .

I chose to start at 89 as rm-nologin runs at S99 and sshd obeys that for non-root users and root can't login via sshd anyways.

I chose K88 for shutdown so it terminates right before syslog shuts down.

---

### Post by TwoWordz on 2006-09-14
Thanks for the reply, I'll edit it. :)

TW

---

### Post by ToonArmy on 2006-09-14
The same can be achieved using [fail2ban]("http://fail2ban.sourceforge.net/") which is apt-get-able from universe. After the default of 5 login attempts it blocks the offending IP using iptables, but its not for everyone.

---

### Post by TwoWordz on 2006-09-14
ToonArmy, thanks for the reply, I'll look at it. 

:)

TW

---

### Post by mbradlcu on 2006-09-15
thanks TwoWordz for the install instructions, also thanks ToonArmy for the fail2ban tip! since it has the choice of iptables or hosts.deny it better fits my needs.

---

### Post by Noiano on 2007-02-22
If I do not allow at all password authentication but only passkey authentication I have nothing to fear, right? I do not need these tools, do I?

---

### Post by Jussi Kukkonen on 2007-02-22
DenyHosts is available in the repositories for Edgy and Feisty, this could maybe be added to the beginning of the HOWTO.

Noiano, you are correct.

---

### Post by TwoWordz on 2007-02-22
Jussi: I've edited the guide, thanks for your input.

TW

---

### Post by TwoWordz on 2007-02-22
Noiano: no you don't need it, it is unlikely that someone can bruteforce your passkey.

TW

---

### Post by 2s4s on 2007-03-12
> Some variables need to be set up before we can start denyhosts:

Code:

SECURE_LOG = /var/log/auth.log
LOCK_FILE = /var/run/denyhosts.pid

And I use:

Code:

BLOCK_SERVICE = ALL

===========
I was not able to follow all the instructions. What shall I do to the quoted part of the instructions?

Thanks for your help.

2s4s

---

### Post by TwoWordz on 2007-03-12
Inside denyhosts.cfg, you will have to change the following entries:

SECURE_LOG = /var/log/auth.log
LOCK_FILE = /var/run/denyhosts.pid
BLOCK_SERVICE = ALL

Just edit the files and change the default settings to the ones I suggest. Secure_log and Lock_file are needed by ubuntu while block_service is just a personal preference.

TW

---

### Post by 2s4s on 2007-03-12
Many thanks for your immediate reply.

I have this error when issuing this command: sudo /etc/init.d/denyhosts start 

> starting DenyHosts:    /usr/bin/env python /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg
Can't read: /private/var/log/system.log
[Errno 2] No such file or directory: '/private/var/log/system.log'
Error deleting DenyHosts lock file: /var/run/denyhosts.pid
[Errno 2] No such file or directory: '/var/run/denyhosts.pid'

I'll do some further test and I'll come back with the results.

---

### Post by TwoWordz on 2007-03-12
Please post your denyhosts.cfg.

Can't read: /private/var/log/system.log

did you change the SECURE_LOG  value to  /var/log/auth.log ?

Also, make sure that you are not editing denyhosts.cfg-dist instead of denyhosts.cfg :)

TW

---

### Post by 2s4s on 2007-03-13
Thanks for the reply.

Sorry my mistake. A typo. The SECURE_LOG portion for Mac OS X (v10.3 or earlier): was enabled, so I disabled it.

I have an error when I run this command: 
update-rc.d denyhosts start 89 2 3 4 5 . stop 88 0 1 6

> update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force

Again, I'll run some tests and I'll come back.

---

### Post by TwoWordz on 2007-03-13
My line was missing a dot, the correct syntax is:

```

update-rc.d denyhosts start 89 2 3 4 5 . stop 88 0 1 6 .

```

TW

---

### Post by slAoD on 2007-03-13
> **2s4s said:**
> Thanks for the reply.

Sorry my mistake. A typo. The SECURE_LOG portion for Mac OS X (v10.3 or earlier): was enabled, so I disabled it.

I have an error when I run this command: 
update-rc.d denyhosts start 89 2 3 4 5 . stop 88 0 1 6



Again, I'll run some tests and I'll come back.

actually you should type a dot (".") in the end of the command...

But after i type this command it tells :  System startup links for /etc/init.d/denyhosts already exist.
I guess this is because i apt-geted it
Is there a chance i could change the priority??(a change in the filename(S20denyhosts ->89denyhosts) would do this?)

---

### Post by 2s4s on 2007-03-13
Hi all, ty for all your quick replies.

Entering this command:
update-rc.d denyhosts start 89 2 3 4 5 . stop 88 0 1 6 .

The output:
Adding system startup for /etc/init.d/denyhosts ...
   /etc/rc0.d/K88denyhosts -> ../init.d/denyhosts
update-rc.d: symlink: Permission denied

So I edited the command to be:
sudo update-rc.d denyhosts start 89 2 3 4 5 . stop 88 0 1 6 .

With the following output:
 Adding system startup for /etc/init.d/denyhosts ...
   /etc/rc0.d/K88denyhosts -> ../init.d/denyhosts
   /etc/rc1.d/K88denyhosts -> ../init.d/denyhosts
   /etc/rc6.d/K88denyhosts -> ../init.d/denyhosts
   /etc/rc2.d/S89denyhosts -> ../init.d/denyhosts
   /etc/rc3.d/S89denyhosts -> ../init.d/denyhosts
   /etc/rc4.d/S89denyhosts -> ../init.d/denyhosts
   /etc/rc5.d/S89denyhosts -> ../init.d/denyhosts

I hope this is the expected behavior.

The last 9 lines of my denyhosts log are the following:
2007-03-14 08:17:20,710 - denyhosts   : INFO     Processing log file (/var/log/auth.log) from offset (12276)
2007-03-14 08:17:20,741 - denyhosts   : INFO     launching DenyHosts daemon (version 2.6)...
2007-03-14 08:17:20,743 - denyhosts   : INFO     DenyHosts daemon is now running, pid: 5883
2007-03-14 08:17:20,744 - denyhosts   : INFO     send daemon process a TERM signal to terminate cleanly
2007-03-14 08:17:20,744 - denyhosts   : INFO       eg.  kill -TERM 5883
2007-03-14 08:17:20,745 - denyhosts   : INFO     monitoring log: /var/log/auth.log
2007-03-14 08:17:20,745 - denyhosts   : INFO     sync_time: 3600
2007-03-14 08:17:20,745 - denyhosts   : INFO     [COLOR="Red"]purging of /etc/hosts.deny is disabled[/COLOR]
2007-03-14 08:17:20,745 - denyhosts   : INFO     [COLOR="Red"]denyhosts synchronization disabled[/COLOR]

Are the lines in red the expected output?

---

### Post by TwoWordz on 2007-03-13
2s4s: looks good!

slAoD: why not try it? :D it should work ;)

TW

---

### Post by 2s4s on 2007-03-13
Thanks all. I finally made it to work  properly.:)

---

### Post by elec999 on 2007-11-17
starting DenyHosts:    /usr/bin/env python /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg
DenyHosts could not obtain lock (pid: )
[Errno 2] No such file or directory: '/var/lock/subsys/denyhosts'

I am getting error when I try to start the Denyhosts.
Thanks

---

### Post by jaigouk on 2008-01-13
Thanks it works!! :guitar:

---

### Post by TwoWordz on 2008-01-13
of course it works :)

TW

---

### Post by umechanism on 2008-03-12
Thanks for the great tips.  However, when I try to start DenyHosts I get the following message:

DenyHosts could not obtain lock (pid: )
[Errno 2] No such file or directory: '/var/lock/subsys/denyhosts'
starting DenyHosts:    /usr/bin/env python /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg

What does that mean?  Yes, I'm a Noob.

Mike

---

### Post by TwoWordz on 2008-03-12
Seems like you skipped a part of the guide 

I added that you need to edit the denyhosts.cfg file, it wasn't clear where to change those:

```

SECURE_LOG = /var/log/auth.log
LOCK_FILE = /var/run/denyhosts.pid

```

Your setup tries to use /var/lock/subsys/denyhost and gets file not found, my guide says the lock file should be /var/run/denyhosts.pid.

Don't worry, we've all been noobs. 

TW

---

### Post by umechanism on 2008-03-12
Thanks for the reply.  I actually copied and pasted the exact phasing our of your post and pasted it into mine at the time of initial setup.  Here is my denyhosts.cfg file
[B][I]
# SECURE_LOG: the log file that contains sshd logging info
# if you are not sure, grep "sshd:" /var/log/*
#
# The file to process can be overridden with the --file command line
# argument
#
# Kubuntu
SECURE_LOG = /var/log/auth.log
LOCK_FILE = /var/run/denyhosts.pid
#
# Mandrake, FreeBSD or OpenBSD: 
#SECURE_LOG = /var/log/auth.log
#
# SuSE:
#SECURE_LOG = /var/log/messages
#
# Mac OS X (v10.4 or greater - 
#   also refer to:   [http://www.denyhosts.net/faq.html#macos](http://www.denyhosts.net/faq.html#macos)
#SECURE_LOG = /private/var/log/asl.log
#
# Mac OS X (v10.3 or earlier):
#SECURE_LOG=/private/var/log/system.log
#[/I][/B]

I think I have exactly what you have.  Let me preface this by saying that I initially set this using the "readme.txt" guide that I downloaded with the softare and I'm only about 80% sure that I did it correctly.  So, is it possible that I have two config files somewhere and they are in conflict?

Thanks again
BTW, I'm using Kubuntu if it matters at all.

Mike

---

### Post by umechanism on 2008-03-13
Anyone?  

The dynyhosts daemon is still not running nor will it start.  All help is greatly appreciated.

Mike

---

### Post by talk2devid on 2010-10-28
Thanks For The Excellent Tutorial.. I Already Go Through HowToForge, Your Tutorial Is Very Easy To Understand and Exactly The Same What I Am Looking Exactly.:):)

---

### Post by P1C0 on 2011-01-01
Actually DenyHosts is in the repositories:
```
sudo apt-get install denyhosts
```

I just wanted to say how much it rocks for saving me from
```
~$ cat /var/log/auth.log | grep "Failed password" | wc -l
2001
```
hack attempts the last 1-2 days.

I had even set a LIMIT rule in ip tables, but some of the attackers only attempted to login every minute or so..

---

