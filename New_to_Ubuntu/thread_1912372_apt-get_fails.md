---
title: "apt-get fails"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by Dubslow on 2012-01-20
```
##############:~&#8752;&#8706; sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libt1-5 libxml2 libxml2-utils python-libxml2 ttf-symbol-replacement-wine1.3 wine1.3
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Failed to exec method /usr/lib/apt/methods/
E: Method  has died unexpectedly!
E: Sub-process  returned an error code (100)
E: Method /usr/lib/apt/methods/ did not start correctly
##############:~&#8752;&#8706;
```

I tried Googling it first, but everything I found mentioned /etc/apt/sources.list, whose contents are posted below. I cannot find anything that would cause any particular instability.

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## This is for digiKam.
# deb http://www.mpe.mpg.de/~ach/kubuntu/edgy ./ # disabled on upgrade to natty
# deb-src http://www.mpe.mpg.de/~ach/kubuntu/edgy ./ # disabled on upgrade to natty
```

No unstable or anything here. Also, Update Manager works just fine and updates everything except the Wine 1.3 packages. I realize that's a beta, but I've had it installed for at least 4 months now, if not closer to 9, and this current problem only showed up in the last day.

---

### Post by /bin/sh on 2012-01-20
Type in
```
sudo apt-get update
```
and try again.

---

### Post by Dubslow on 2012-01-20
I would have felt really dumb if that had worked, but fortunately for my ego, (unfortunately in terms of fixing it) it did not.

---

