---
title: "Not allowing me to remove"
date: 2006-06-28
forum: Repositories &amp; Backports
---

### Post by PoisoN2003 on 2006-06-28
Hey i tried to install gaim and it gave me an error at the end 
but its not only gaim it gives me that everytime i try to install or remove anything
i tried removing it with sudo apt-get remove i tried repo i checked if anything is broken
```
poison@ubuntu:~$ sudo apt-get install gaim
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  libzephyr3
The following NEW packages will be installed
  gaim
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/1288kB of archives.
After unpacking 3670kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gaim
Install these packages without verification [y/N]? y
Selecting previously deselected package gaim.
(Reading database ... 184638 files and directories currently installed.)
Unpacking gaim (from .../gaim_1%3a1.9.99.is.2.0.0+beta3-1ubuntu1_i386.deb) ...
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Setting up rageircd (2.0.1-5) ...
Adding system user
adduser: Warning: The home dir you specified already exists.
Allowing use of questionable username.
The user `Debian-rageircd' already exists as a system user. Exiting...
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "start" failed.
dpkg: error processing rageircd (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gaim (1.9.99.is.2.0.0+beta3-1ubuntu1) ...

Errors were encountered while processing:
 clvm
 rageircd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is what i always get
E: Sub-process /usr/bin/dpkg returned an error code (1)
i dont know what it is so if anyone could help i would really appreciate it

I also get this in the repo menu when removing something
```
E: clvm: subprocess post-installation script returned error exit status 3
E: rageircd: subprocess post-installation script returned error exit status 1
```

---

### Post by cantormath on 2006-07-19
I have the same error regarding clvm

---

### Post by kf_spif on 2006-07-22
same for me... But, check there [http://www.ubuntuforums.org/archive/index.php/t-186356.html](http://www.ubuntuforums.org/archive/index.php/t-186356.html)

---

