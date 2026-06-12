---
title: "I cant install yelp-dbgsym because of dependencies"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by madsc89 on 2008-10-26
I am trying to perform a backtrace, but I can't install yelp-dbgsym!

I followed this guide: [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

When I try to mark it for installation in synaptic, I get this message: "The following packages have unresolvable dependencies. Make sure that all the required repositories are added and enabled in the preferences.
yelp-dbgsym:
Depends: yelp (=2.22.1-0ubuntu2) but 2.22.1-0ubuntu2.8.04.3 is to be installed"

All repos are enabled.

When I then try to force yelp (=2.22.1-0ubuntu2), I have to mark the following for removal:

firefox, firefox-3.0, firefox-3.0-gnome-support, firefox-gnome-support, gnome-user-guide, sun-java6-plugin, ubufox, ubuntu-docs, xulrunner-1.9, xulrunner-1.9-gnome-support.

It is obvious I don't want to remove those. So then I'm stuck.

How can I install yelp-dbgsym or something equal?

Thank you.

---

### Post by ashmew2 on 2008-10-26
do check that the repositories you added are for Hardy (if you are using Hardy) or Gutsy ( if you are on Gutsy) in /etc/apt/sources.list..
```

sudo apt-get install -f
```

might help (although its unlikely)..

---

### Post by ibuclaw on 2008-10-26
Do you have any external sources in your apt sources lists?

Ubuntu Backports... Ubuntu Proposed?

Regards
Iain

---

### Post by madsc89 on 2008-10-26
I'm not at home right now, but I'm pretty sure I've got proposed and some others like that, yes.

---

### Post by madsc89 on 2008-10-27
This is my sources.list:
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://no.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

deb http://ddebs.ubuntu.com hardy main universe
deb http://ddebs.ubuntu.com hardy-updates main universe
deb http://ddebs.ubuntu.com hardy-proposed main universe
deb http://ddebs.ubuntu.com hardy-security main universe
```

Am I not supposed to have some of them?

---

### Post by madsc89 on 2008-10-28
bump

---

