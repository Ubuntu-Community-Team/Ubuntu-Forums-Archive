---
title: "Help! Ppa chroot problem!"
date: 2010-02-17
forum: Packaging and Compiling Programs
---

### Post by bilalakhtar on 2010-02-17
Hi, guys, I have a PPA here:-
[https://launchpad.net/~gnome-media-player-development/+archive/development](https://launchpad.net/~gnome-media-player-development/+archive/development)
I have been trying to compile a package for lucid in it.
The package compiles fine for lucid amd64 but not for i386, saying "Chroot problem". Below is the traceback.
```
Fetched 49.2MB in 2s (22.1MB/s)
E: Could not perform immediate configuration on 'udev'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
RUN: /usr/share/launchpad-buildd/slavebin/scan-for-processes ['/usr/share/launchpad-buildd/slavebin/scan-for-processes', '1513745-3096343']
Scanning for processes to kill in build /home/buildd/build-1513745-3096343/chroot-autobuild...
RUN: /usr/share/launchpad-buildd/slavebin/umount-chroot ['umount-chroot', '1513745-3096343']
Unmounting chroot for build 1513745-3096343...

```
Find the full log at
[http://launchpadlibrarian.net/39301188/buildlog_ubuntu-lucid-i386.gnome-media-player_0.1-1bzr25~lucid3_CHROOTWAIT.txt.gz](http://launchpadlibrarian.net/39301188/buildlog_ubuntu-lucid-i386.gnome-media-player_0.1-1bzr25~lucid3_CHROOTWAIT.txt.gz)

---

### Post by SevenMachines on 2010-02-17
this may be a temporary technical issue with the build farm at the moment. having just seen something similar myself on an archive upload on amd64 and sparc.

---

### Post by SevenMachines on 2010-02-17
hi, it seems there was a udev upgrade bug on the build system. this should be fixed soon. its not a problem with your package though.

---

### Post by bilalakhtar on 2010-02-18
Yes, it has been fixed. I reuploaded, and the build worked!

---

