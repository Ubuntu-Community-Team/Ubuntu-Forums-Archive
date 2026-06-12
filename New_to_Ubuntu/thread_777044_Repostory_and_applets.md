---
title: "Repostory and applets"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by shoaibi on 2008-05-01
why is this link not working:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

then can anyone give me some nice and handy (even if long) list of repositories of nice softwares? coz my favourite link [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) is down...


aaahhh and secondly, just finished my new 8.04 install, now whenever i add an applet to the panels which is part of "Application Launcher" a question mark appears with name as (null) and description as open /usr/share/applications/appname.desktop. I even killed gnome panels, and restarted computer, still no use....

---

### Post by Perfect Storm on 2008-05-01
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta amd64 (20080319)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://dk.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy universe
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

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

## Viewizard Games repository
deb http://viewizard.com/linux debian/

## 465 Free Fonts
deb http://ppa.launchpad.net/corenominal/ubuntu gutsy main
deb-src http://ppa.launchpad.net/corenominal/ubuntu gutsy main

```

Wine: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Medibuntu: [http://www.medibuntu.org/](http://www.medibuntu.org/)
Cinelerra: [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

---

