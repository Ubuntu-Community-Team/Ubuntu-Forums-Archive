---
title: "Needed to optimize and have an up-to-date Hardy?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2008-09-20
I'm always searching for and installing the most up-to-date tools to optimize Hardy's performance from the power button to the software sources.  I love how the repositories work and just wanted to know if the list I have given below is all I need, or if there are others that could or should be added to quench my thirst for having the smoothest computer out there. Thank you for your help!!

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) (source code)
[http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu)
[http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu)
[http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) (source code)
[http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu)
WineHQ - Ubuntu 8.04 "Hardy Heron"
WineHQ - Ubuntu 8.04 "Hardy Heron" (source code)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) (source code)

---

### Post by Pro-reason on 2008-09-20
There are hundreds of repos that you could add, but the more you add, the greater the chance of some sort of conflict, or of buggy software.

---

### Post by zvacet on 2008-09-20
@ **FAMUgolfer**

```
cat etc/apt/sources.list
```

Post it here.

---

### Post by Nepherte on 2008-09-20
Ubuntu's release model typically doesn't work with the most up-to-date packages. For every release they freeze the features/version of the included software to guarantee everything works smooth together. The updates provided by the official repositories typically offer security and bug fixes and rarely the latest version of a piece of software. If that's what you're after, I'm afraid you'll have to look in the ppa repositories or sites as getdeb. You can of course also compile the latest software yourself although that might be a little more difficult.

If you just want an up-to-date hardy, be sure to enable the universe and multiverse repositories, as well as backports (the last one is not suported by ubuntu and *might* cause a system break, although I rarely saw any. In any case you're warned). I don't recommend you enable the proposed repository. You can consider that one was as a repository for testing and debugging purposes. Some programs such as deluge torrent also have their own ppa repository that includes the latest version. Here's a list with ppa's: [http://ubuntuforums.org/showthread.php?p=5469046](http://ubuntuforums.org/showthread.php?p=5469046)

---

### Post by FAMUgolfer on 2008-09-23
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) hardy main
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main

---

