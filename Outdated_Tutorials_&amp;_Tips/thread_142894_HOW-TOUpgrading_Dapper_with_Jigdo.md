---
title: "HOW-TO:Upgrading Dapper with Jigdo"
date: 2006-03-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Hello World on 2006-03-11
Jigdo is a program which you can download only updated packages and merge with available packages for building isos. Today, Dapper Flight 5 is ready for testers. If you have previous Flight release you can use available packages in cd instead of downloading whole Flight 5 iso. Or you can use updated packages in your /var/cache/apt/archives/ directory. 

First install jigdo-file;

```
sudo apt-get install jigdo-file
```

download .jigdo and .template file from [http://cdimage.ubuntu.com/releases/dapper/flight-5/](http://cdimage.ubuntu.com/releases/dapper/flight-5/) (you can use [ftp://cdimage.ubuntulinux.org/cdimage/daily/current/](ftp://cdimage.ubuntulinux.org/cdimage/daily/current/) address later). For i386 architecture,

```
dapper-install-i386.jigdo 
dapper-install-i386.template
``` 

Let's start jigdo,
```
jigdo-lite dapper-install-i386.jigdo
```

we should show our package directory or cd 

Files to scan: /media/cdrom (for cd)

Files to scan: /var/cache/apt/archives/ (for updated packages)

Files to scan: just press enter

Debian mirror: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) (for downloading rest of packages)

after some time (lesser then whole download process) you can see dapper-install-i386.iso in your Home directory.

---

### Post by Hello World on 2006-04-02
Jigdo program builds a dapper-install-i386.iso.tmp file in your home directory. If your downloading interrupts, you can use packets in this file with changing name to dapper-install-i386.iso, then extract pool directory, then show directory to jigdo program. 

Rsync sometimes needed to complete process. After building your dapper-install-i386.iso.tmp, rename again to dapper-install-i386.iso and run rsync:
```
rsync -v --progress rsync://cdimage.ubuntu.com/cdimage/daily/current/dapper-install-i386.iso dapper-install-i386.iso dapper-install-i386.iso
``` If you have a firewall, just open port 873 for rsync.

---

