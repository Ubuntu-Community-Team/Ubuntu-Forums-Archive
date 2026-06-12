---
title: "Glibc required!"
date: 2006-07-26
forum: Repositories &amp; Backports
---

### Post by Mathiasdm on 2006-07-26
I'm trying to install the Anjuta editor.

Something went wrong, and the program started complaining about several dependencies missing.
I installed most of them, but there's not 'glibc' I can find to install (I'm using Synaptic).

Feel free to throw cryptic commands at me, I don't mind.

Any ideas?

---

### Post by jordilin on 2006-07-26
Do you have enabled the common repos, such as universe and multiverse? Show us your sources.list.

---

### Post by Mathiasdm on 2006-07-28
Okay, turns out it was glib, not glibc.

Here's sources.list:
```


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://be.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://be.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb http://be.archive.ubuntu.com/ubuntu/ dapper universe
## deb-src http://be.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
## deb http://security.ubuntu.com/ubuntu dapper-security universe
## deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

## Automatix repository:
deb http://www.beerorkid.com/automatix/apt dapper main

## XGL:
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

## Commercial:
deb http://archive.canonical.com/ubuntu dapper-commercial main


```
Oh, and it seems I have libglib-2.0-0 installed.
However, I still get the error message.

---

### Post by geoffkaniuk on 2006-07-31
> **Mathiasdm said:**
> Okay, turns out it was glib, not glibc.

Here's sources.list:
```


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://be.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://be.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb http://be.archive.ubuntu.com/ubuntu/ dapper universe
## deb-src http://be.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
## deb http://security.ubuntu.com/ubuntu dapper-security universe
## deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

## Automatix repository:
deb http://www.beerorkid.com/automatix/apt dapper main

## XGL:
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

## Commercial:
deb http://archive.canonical.com/ubuntu dapper-commercial main


```
Oh, and it seems I have libglib-2.0-0 installed.
However, I still get the error message.
I had the same problem.  libglib2.0 is the run time library.

You need libglib2.0-dev installed to get the header files for actual program development.

Good luck.

---

### Post by Mathiasdm on 2006-08-03
Thanks!

---

