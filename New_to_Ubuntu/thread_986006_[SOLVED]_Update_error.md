---
title: "[SOLVED] Update error"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-11-18
Hello guys!

I get a strange error when I try to update my system
```
W: Failed to fetch http://playonlinux.botux.net/dists/hardy/Release.gpg  Could not resolve 'playonlinux.botux.net'

W: Failed to fetch http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_US.bz2  Could not resolve 'playonlinux.botux.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.
``` 

I looked through all my repositories and I can't find this one to delete it.This is my list:
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ro.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted #Added by software-properties
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe #Added by software-properties

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted #Added by software-properties
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://ppa.launchpad.net/gilir/ubuntu hardy main universe
#deb http://security.debian.org/ etch/updates main contrib non-free
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
#deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main
deb http://ppa.launchpad.net/starfall87/ubuntu hardy main
deb-src http://ppa.launchpad.net/starfall87/ubuntu hardy main
``` 

Am I blind?
Thanks!

---

### Post by beercz on 2008-11-18
Try commenting out some of the deb lines - especially from launchpad and budgetdedicated - then try again.

A process of elimination will eventually route out the rogue repository.

---

### Post by Dedoimedo on 2008-11-18
Hello,

That happens to me when I'm on wireless on a specific guest network where you have to authenticate every once in a while, due to security and proxy issues. This occurs after I've had connection and it drops. Only on wireless...

I solve the problem by establishing an http connection via browser, then running sudo apt-get update.

Maybe my solutions sounds stupid, but ... anyhow, Internet works?

Dedoimedo

---

### Post by drs305 on 2008-11-18
This repository may not plant itself within the sources.list file. Use a file browser and check to see if a /etc/apt/sources.list.d/playonlinux... folder or file was created, similar to how medibuntu does it. If you find one, try moving it/deleting it/etc to solve your problem or open it up and edit the offending lines.

---

### Post by Troll_the_Great on 2008-11-18
> **drs305 said:**
> This repository may not plant itself within the sources.list file. Use a file browser and check to see if a /etc/apt/sources.list.d/playonlinux... folder or file was created, similar to how medibuntu does it. If you find one, try moving it/deleting it/etc to solve your problem or open it up and edit the offending lines.

Thanks, that did it.For some strange reason, I couldn't move the files (it says "Permission denied" even though I opened nautilus as root) so I opened the files and put an "#" in front of the lines.That took care of my problem.
Weird about the permission issue though...
Thanks again!

---

