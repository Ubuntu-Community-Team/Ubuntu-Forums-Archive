---
title: "ubuntu software manager not working"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by navvirdi15 on 2012-03-30
both software manager and synaptic manager not opening
receiving the error


E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/n-muench-vlc-oneiric.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by arochester on 2012-03-30
You have a mistake in your sources list. How you fix this can depend on the Package Manager(s) that you use. 

To go straight to the sources list, open a Terminal and issue the command:> gksudo gedit /etc/apt/sources.listLook at line 3. You can disable the whole line by putting a # at the beginning of the line or you can edit/correct it.

If you are in any doubt copy and paste your whole sources list here so we can have a look.

---

### Post by nothingspecial on 2012-03-30
Changed thread prefix from lubuntu to ubuntu

---

### Post by garvinrick4 on 2012-03-30
If you are having any trouble use this line of code in a terminal. 

```
gksudo gedit /etc/apt/sources.list.d/n-muench-vlc-oneiric.list
```Put the # (comment sign) in front of offending line  hit save as instructed in previous post.

---

### Post by navvirdi15 on 2012-03-31
my sources list

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-proposed restricted main multiverse universe



n-muench-vlc-oneiric.list

deb [http://ppa.launchpad.net/n-muench/vlc/ubuntu](http://ppa.launchpad.net/n-muench/vlc/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/n-muench/vlc/ubuntu](http://ppa.launchpad.net/n-muench/vlc/ubuntu) oneiric main
ain

---

### Post by Baldrick_NZ on 2012-03-31
> **navvirdi15 said:**
> 
n-muench-vlc-oneiric.list

deb [http://ppa.launchpad.net/n-muench/vlc/ubuntu](http://ppa.launchpad.net/n-muench/vlc/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/n-muench/vlc/ubuntu](http://ppa.launchpad.net/n-muench/vlc/ubuntu) oneiric main
ain

Delete only the 'ain' part right at the end, and save.
logout and back in again, then run update manager again. 

Should fix your problem.

---

### Post by navvirdi15 on 2012-03-31
it solved ,thanks
but can u explain how?
and how ain got to that place?

---

### Post by arochester on 2012-03-31
(m)ain?

---

