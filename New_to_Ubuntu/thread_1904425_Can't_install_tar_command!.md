---
title: "Can't install tar command!"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by stamatiou on 2012-01-04
I have recently installed xubuntu but when i execute the tar command, even with the v option it stucks and it does not show me anything! So I tried to uninstall the tar command by using sudo apt-get remove --purge tar (extreemly stupid! I know!). Know when I type sudo apt-get install tar i get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tsocks socat libreadline5
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ncompress
The following NEW packages will be installed:
  tar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/202 kB of archives.
After this operation, 684 kB of additional disk space will be used.
dpkg: warning: 'tar' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by kerry_s on 2012-01-04
sudo apt-get -f install

---

### Post by stamatiou on 2012-01-04
> **kerry_s said:**
> sudo apt-get -f install
I have tried it :( It does not install anything and nothing changes...
But thanks for the fast reply!

---

### Post by TBABill on 2012-01-04
Same result using Synaptic or Ubuntu Software Center?

---

### Post by josephmills on 2012-01-04
> **stamatiou said:**
> I have recently installed xubuntu but when i execute the tar command, even with the v option it stucks and it does not show me anything! So I tried to uninstall the tar command by using sudo apt-get remove --purge tar (extreemly stupid! I know!). Know when I type sudo apt-get install tar i get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tsocks socat libreadline5
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ncompress
The following NEW packages will be installed:
  tar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/202 kB of archives.
After this operation, 684 kB of additional disk space will be used.
dpkg: warning: 'tar' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

could we see 
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/
```

---

### Post by stamatiou on 2012-01-04
> Same result using Synaptic or Ubuntu Software Center?
Yes :(

> **josephmills said:**
> could we see 
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/
```
/etc/apt/sources.list:
```
# deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```
ls /etc/apt/sources.list:
```
/etc/apt/sources.list
```

---

### Post by Buntumatic on 2012-01-04
Methinks tar may be required to install tar.
If that's true then you need to copy tar binary from another computer.

---

### Post by josephmills on 2012-01-04
here  you go please read 2x before saying that this wont work [TAR](http://www.gnu.org/software/tar/)

---

### Post by Buntumatic on 2012-01-04
Yep, that will work if you still have gzip installed. :) Don't get too new one, it may be compiled against newer glibc than yours.

---

### Post by stamatiou on 2012-01-05
So how can I install it after downloading from the gnu site?

---

### Post by Buntumatic on 2012-01-05
I'd put the executable in /usr/local/bin, then reinstall tar, after you are sure install was successful remove it.

---

### Post by stamatiou on 2012-01-05
Which of the files should I download? There are too many! I have downloaded one which when extracted with gui it has .diff ending :/

---

### Post by Buntumatic on 2012-01-05
Wait a minute ... those are sources, do you have GCC installed?

---

### Post by stamatiou on 2012-01-05
Yes. But which one should I download? I am in [ftp://ftp.ntua.gr/pub/gnu/tar/](ftp://ftp.ntua.gr/pub/gnu/tar/)

---

### Post by Buntumatic on 2012-01-05
This should do: [ftp://ftp.ntua.gr/pub/gnu/tar/tar-1.26.tar.gz](ftp://ftp.ntua.gr/pub/gnu/tar/tar-1.26.tar.gz)

---

### Post by stamatiou on 2012-01-05
And how can I extract it?

---

### Post by Buntumatic on 2012-01-05
Look, I have to go to work, I've put a 32-bit tar executable into my router for download, it's from Gentoo and may or may not work with your Ubuntu.

Link: [tar.gz]("http://saul.homeunix.org:8000/tmp/tar.gz")

---

### Post by stamatiou on 2012-01-05
No, it didn't work :(
But although thanks for the time you spend :D

---

### Post by stamatiou on 2012-01-05
It's ok now, I reinstalled Xubuntu :D But in case something like that happens again, is there a way i can restore my system to a previous condition?

---

### Post by Buntumatic on 2012-01-05
:oops: Now when you said you reinstalled I suddenly realized you had install CD! All you had to do was to copy the tar from the CD ...

---

### Post by kerry_s on 2012-01-05
> **Buntumatic said:**
> :oops: Now when you said you reinstalled I suddenly realized you had install CD! All you had to do was to copy the tar from the CD ...

lol, sometimes the answer is just to simple. :-)

---

### Post by stamatiou on 2012-01-06
I reinstaled it with a usb created with Linux Live USB Creator, would I still be able to find the tar?

---

### Post by Buntumatic on 2012-01-06
Yep, do not know what it exactly looks like, but after mounting it tar is there.

---

