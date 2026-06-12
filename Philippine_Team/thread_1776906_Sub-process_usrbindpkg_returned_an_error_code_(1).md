---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-06-06
forum: Philippine Team
---

### Post by k1ll3rwh4l3 on 2011-06-06
Hello, 

I have a problem with my n900..

"Sub-process /usr/bin/dpkg returned an error code (1)" 


Nokia-N900:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up account-plugin-salut (0.10) ...
/var/lib/dpkg/info/account-plugin-salut.postinst: line 6: /etc/init.d/avahi-daemon: not found
dpkg: error processing account-plugin-salut (--configure):
subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of telepathy-extras:
telepathy-extras depends on account-plugin-salut; however:
Package account-plugin-salut is not configured yet.
dpkg: error processing telepathy-extras (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
account-plugin-salut
telepathy-extras
E: Sub-process /usr/bin/dpkg returned an error code (1)
Nokia-N900:~# 

The help is welcome!

---

### Post by Script Warlock on 2011-06-07
n900 running ubuntu?

---

