---
title: "Upgrade error"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by KocetoNs on 2008-04-25
I have clean installation of kubuntu 8.04 beta.
But when i try to upgrade i get this error
```
339 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
Need to get 2897kB/350MB of archives.
After this operation, 60.8MB of additional disk space will be used.
Get:1 http://bg.archive.ubuntu.com hardy/main python2.5 2.5.2-2ubuntu4 [2897kB]
Fetched 2897kB in 1s (2521kB/s)
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 81318 files and directories currently installed.)
Preparing to replace libc6 2.7-9ubuntu2 (using .../libc6_2.7-10ubuntu3_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libc6_2.7-10ubuntu3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.7-10ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ace007 on 2008-04-25
close all other synaptic applications or any other application that is running any kind of installer

---

### Post by KocetoNs on 2008-04-25
there are no synaptic applications running 
i`ve just booted the system and tried to do the upgrade

---

