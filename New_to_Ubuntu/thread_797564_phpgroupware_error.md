---
title: "phpgroupware error?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by AbyssWolf1105 on 2008-05-17
I've been trying to download WoW on my computer for the past god knows how many hours, I started last night at 9pm, and worked till 2am. Said forget it and went to bed. I woke up and decided to try again before I go to work. (I work at one of the two major dueling computer distributing companys, just going to say my colors red) So I was going to take my compy in and see if any of the techs could help me figure this stuff out. 

So, here's the error I keep getting... Which is making me want to pull the little hair I have left, out.
```

Writing extended state information... Done
Setting up phpgroupware (0.9.16.012+dfsg-1) ...
setting up apache
setting up apache-ssl
setting up apache-perl
setting up apache2
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
dpkg: error processing phpgroupware (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of phpgroupware-fudforum:
 phpgroupware-fudforum depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-fudforum (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-sitemgr:
 phpgroupware-sitemgr depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-sitemgr (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phpgroupware
 phpgroupware-fudforum
 phpgroupware-sitemgr
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up phpgroupware (0.9.16.012+dfsg-1) ...
setting up apache
setting up apache-ssl
setting up apache-perl
setting up apache2
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
dpkg: error processing phpgroupware (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of phpgroupware-sitemgr:
 phpgroupware-sitemgr depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-sitemgr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-fudforum:
 phpgroupware-fudforum depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-fudforum (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phpgroupware
 phpgroupware-sitemgr
 phpgroupware-fudforum
Reading package lists... Done 
```  

I was updating with the *sudo apt-get update* when I got the error message

Help please guys? I need my WoW fix soon.

---

### Post by AbyssWolf1105 on 2008-05-19
Ok, to everyone who looked at this forum topic and didn't say anything to it, shame.
Cause, I'm starting to go a bit crazy and get a bit angry.

Got the same message again. Trying to download firestarter...

```
k@tank-laptop:~$ sudo apt-get install firestarter
[sudo] password for tank:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  dhcp3-server
The following NEW packages will be installed:
  firestarter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 409kB of archives.
After unpacking 2011kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com gutsy/universe firestarter 1.0.3-5ubuntu1 [409kB]
Fetched 409kB in 2s (164kB/s)       
Selecting previously deselected package firestarter.
(Reading database ... 123240 files and directories currently installed.)
Unpacking firestarter (from .../firestarter_1.0.3-5ubuntu1_amd64.deb) ...
Setting up phpgroupware (0.9.16.012+dfsg-1) ...
setting up apache
setting up apache-ssl
setting up apache-perl
setting up apache2
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
dpkg: error processing phpgroupware (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of phpgroupware-fudforum:
 phpgroupware-fudforum depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-fudforum (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-sitemgr:
 phpgroupware-sitemgr depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-sitemgr (--configure):
 dependency problems - leaving unconfigured
Setting up firestarter (1.0.3-5ubuntu1) ...

Errors were encountered while processing:
 phpgroupware
 phpgroupware-fudforum
 phpgroupware-sitemgr
E: Sub-process /usr/bin/dpkg returned an error code (1)
tank@tank-laptop:~$ 
```


So what of it guys? I've got a rewrite disc in my hand for windows xp, and if I can't figure it out within the next 24, it's back to what I know

---

