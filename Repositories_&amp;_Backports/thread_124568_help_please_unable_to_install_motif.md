---
title: "help please: unable to install motif"
date: 2006-02-01
forum: Repositories &amp; Backports
---

### Post by dabd on 2006-02-01
I am having trouble installing motif libraries, which I need for Opera browser.
I followed the Opera browser wiki instructions but I get an error when I type:

```
~$ sudo apt-get install openmotif lesstif1 lesstif2 motif-clients

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package openmotif
```

This is my sources.list:

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://pt.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pt.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://pt.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://pt.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://pt.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://pt.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe


deb http://deb.opera.com/opera/ unstable non-free
```

---

