---
title: "problem with upgrading plasma widget addons"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Ryu Hayabusa on 2012-01-30
First I'm so noobie at ficking packages installations and managment
,recently i have been trying to upgrade and install new version of plasma widgets addons,so I have tried that with terminal but resulted with the following outcome




sudo apt-get install plasma-widgets-addons
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  plasma-widgets-addons
0 upgraded, 1 newly installed, 0 to remove and 43 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,509 kB of archives.
After this operation, 5,837 kB of additional disk space will be used.
(Reading database ... 380208 files and directories currently installed.)
Unpacking plasma-widgets-addons (from .../plasma-widgets-addons_4%3a4.8.0-0ubuntu1~oneiric1~ppa3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/plasma-widgets-addons_4%3a4.8.0-0ubuntu1~oneiric1~ppa3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/kde4/plasma_applet_icontasks.so', which is also in package plasma-widget-icon-tasks 0.9.2-0ubuntu0~gnumdk2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/plasma-widgets-addons_4%3a4.8.0-0ubuntu1~oneiric1~ppa3_i386.deb
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

