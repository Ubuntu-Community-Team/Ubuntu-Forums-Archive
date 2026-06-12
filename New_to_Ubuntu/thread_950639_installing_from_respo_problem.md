---
title: "installing from respo problem"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by ja660k on 2008-10-17
hey guys, im having a problem with installing some apps from the package manager.

id didnt use to be a problem, but now i would want this piece of software and what i get is this:

```

Could not mark all packages for installation
the following packages have unresolvable dependencies.
Make sure that all required repositories are added and embedded in the preferences

netbeans:
 Depends: libnb-apisupport1-java but it is not going to be installed
 Depends: libnb-ide8-java but it is not going to be installed
 Depends: libnb-java1-java but it is not going to be installed

```

i have done some editing to the sources list...
when i terminal sudo apt-get update one package is stuck on 99%
and eventually i get fed up and exit

where can i find the original sourcelist that comes when i first install the os

---

### Post by eternalnewbee on 2008-10-17
> **ja660k said:**
> hey guys, im having a problem with installing some apps from the package manager.

id didnt use to be a problem, but now i would want this piece of software and what i get is this:

```

Could not mark all packages for installation
the following packages have unresolvable dependencies.
Make sure that all required repositories are added and embedded in the preferences

netbeans:
 Depends: libnb-apisupport1-java but it is not going to be installed
 Depends: libnb-ide8-java but it is not going to be installed
 Depends: libnb-java1-java but it is not going to be installed

```

i have done some editing to the sources list...
when i terminal sudo apt-get update one package is stuck on 99%
and eventually i get fed up and exit

where can i find the original sourcelist that comes when i first install the os

You could look for  
Depends: libnb-apisupport1-java but it is not going to be installed
 Depends: libnb-ide8-java but it is not going to be installed
 Depends: libnb-java1-java but it is not going to be installed
in synaptic.
If they are not there, then it is possible that...
Well, there is always more than one possible answer, so it could be the site you are getting it from, or compatibility, or a legal issue...
I don't know...
Patience is a virtue... Live and learn through trial and error, and wait for more knowledgeable users' advice.
Good luck.

---

### Post by wolfen69 on 2008-10-17
i don't know if you live in the us, but here is one:
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20080222)]/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

---

### Post by Bucky Ball on 2008-10-17
lol wolfen69, how's your current status! lmfao

---

