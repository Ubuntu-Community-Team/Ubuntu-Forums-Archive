---
title: "Ign in apt-get update"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by shoaibi on 2008-08-28
How to avoid those Ignored ones? i mean how to also get them?

My Repo list:
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Viewizard Games Repository
## wget http://www.viewizard.com/linux/viewizard-gpg.asc
## sudo apt-key add viewizard-gpg.asc
# deb http://viewizard.com/linux debian/

## Mediubuntu needs key:
## wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
deb http://packages.medibuntu.org/ hardy free non-free

## Google Repos
## Key: wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
# deb http://dl.google.com/linux/deb/ stable non-free

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

## Wicd network manager
deb http://apt.wicd.net hardy extras

## DTC
# deb ftp://ftp.gplhost.com/debian/ stable main

## FreeMind Repositories
deb http://eric.lavar.de/comp/linux/debian/ unstable/
deb http://eric.lavar.de/comp/linux/debian/ ubuntu/


## Pix Bros
## Damn Slow Servers :( :'(
# deb http://fr.archive.ubuntu.com/ubuntu intrepid main universe

deb http://ppa.launchpad.net/corenominal/ubuntu hardy main
deb-src http://ppa.launchpad.net/corenominal/ubuntu hardy main
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe

```

What i get:
```

13:24:38] shoaibi@cosp-hq ~/Desktop $ alias sagu="sudo apt-get update"
13:25:02] shoaibi@cosp-hq ~/Desktop $ sagu >> sagu.out && cat sagu.out | grep Ign
Ign http://archive.canonical.com hardy/partner Translation-en_US
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US
Ign http://eric.lavar.de unstable/ Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://apt.wicd.net hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Ign http://wine.budgetdedicated.com hardy/main Packages
Ign http://eric.lavar.de unstable/ Translation-en_US
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://apt.wicd.net hardy/extras Translation-en_US
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Ign http://ppa.launchpad.net hardy/main Sources
Ign http://eric.lavar.de ubuntu/ Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-proposed/multiverse Translation-en_US
Ign http://eric.lavar.de ubuntu/ Translation-en_US
Ign http://us.archive.ubuntu.com hardy-proposed/universe Translation-en_US
Ign http://eric.lavar.de ubuntu/ Release
Ign http://eric.lavar.de unstable/ Packages
Ign http://eric.lavar.de ubuntu/ Packages

```

---

### Post by eightmillion on 2008-08-28
These are normal. They indicate that nothing has changed in that repository since you last checked.

---

### Post by stucky on 2008-12-10
You could always try to run the following prior to apt-get update

```
$ unset LANG LANGUAGE
```

---

