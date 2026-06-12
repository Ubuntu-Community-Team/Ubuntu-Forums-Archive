---
title: "software center issue"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by THEDUDE61636 on 2011-09-10
hi
when i try installing any program from it
i get this message
see the attachment

---

### Post by llamabr on 2011-09-10
Are you sure you have internet connection on that machine?

open a terminal, and type:

```
cat /etc/apt/sources.list
```

and post the output.  What are you trying to install?

---

### Post by THEDUDE61636 on 2011-09-10
yes i am sure have an Internet connection on this (that) machine 
and here is the output
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://iq.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://iq.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://iq.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://iq.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://iq.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://iq.archive.ubuntu.com/ubuntu/ natty universe
deb http://iq.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://iq.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://iq.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://iq.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://iq.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://iq.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://iq.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://iq.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

```

---

### Post by Paqman on 2011-09-10
Have you tried switching to a different download server? In Ubuntu Software Centre go to Edit > Software Sources > Download from > Other > Select best server

---

