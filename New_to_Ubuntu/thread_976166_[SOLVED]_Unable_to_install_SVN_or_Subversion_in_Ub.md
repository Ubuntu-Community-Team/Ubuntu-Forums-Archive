---
title: "[SOLVED] Unable to install SVN or Subversion in Ubuntu 8.04 LTS"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by fr.theo on 2008-11-09
I have tried to install the application called subversion as some programs and installation procedures require it, however I can not due to the following error:

subversion:
 Depends: libsvn1 but it is not going to be installed


I have tried to install it dependencies but every time I select the required dependency it still refuses to install? I am at a loss any help.

---

### Post by hyper_ch on 2008-11-09
how do you try to install it?

---

### Post by fr.theo on 2008-11-09
I have tried two ways:

1. through Applications >> Add/Remove

2. through Terminal sudo apt-get install subversion


but each one tells me that there is a conflicting application and goto synaptic Package manager to resolve it, however when I search for SVN I select its install and it tells me that certain dependencies are required and when I attempt to install them I get the message which I placed in the first post.

---

### Post by hyper_ch on 2008-11-09
what's the content for your /etc/apt/sources.list ?

---

### Post by fr.theo on 2008-11-09
here is the contents of my sources.list

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ hardy restricted main
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates restricted main
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security restricted main
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu gutsy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse


deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main

deb http://ppa.launchpad.net/c-korn/ubuntu hardy main
deb-src http://ppa.launchpad.net/c-korn/ubuntu hardy main
deb http://fr.archive.ubuntu.com/ubuntu hardy universe
deb http://fr.archive.ubuntu.com/ubuntu hardy universe
```

---

### Post by mc4man on 2008-11-09
The odds are this resolved itself, if not then note that you have the korn ppa enabled as a source.
That repo includes subversion and libsvn1 in higher versions than hardy. 
Search in synaptic for svn and see what's installed and the versions avail.(subversion and libsvn1 must be same ver. #

---

### Post by fr.theo on 2008-11-10
> The odds are this resolved itself, if not then note that you have the korn ppa enabled as a source.
That repo includes subversion and libsvn1 in higher versions than hardy.
Search in synaptic for svn and see what's installed and the versions avail.(subversion and libsvn1 must be same ver. #

nothing i cant see that would be conflicting with the svn or at least any thing I can understand, I also searched for the Korn but nothing there was installed?

---

### Post by fr.theo on 2008-11-10
I have resolved this issue by downloading manually the files required to install the packages from the ubuntu site: [http://packages.ubuntu.com/gutsy/devel/subversion](http://packages.ubuntu.com/gutsy/devel/subversion).

just a note download each dependency deb file individually and install them according to the systems requirement. eg. libsvn1 then  libpq5 and so on.


thanks for all your help.

---

