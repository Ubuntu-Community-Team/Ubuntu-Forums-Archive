---
title: "unable to upgrade to 13.04"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by Trig007 on 2013-05-11
I'm hoping someone can help. trying to upgrade to 13.04 from 12.10, but keep getting the same error:

W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources)  404  Not Found 
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages)  404  Not Found 
, E:Some index files failed to download. They have been ignored, or old ones used instead.

can anyone help, this is driving me crazy, really don't want to have to do a clean install unless there is no other way

---

### Post by JRV on 2013-05-11
There are errors in your /etc/apt/sources.list file.

Post a copy of the file here.

---

### Post by Trig007 on 2013-05-11
# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-proposed restricted main universe multiverse

# deb [http://ppa.launchpad.net/wii.sceners.linux/wiithon-1.1/ubuntu](http://ppa.launchpad.net/wii.sceners.linux/wiithon-1.1/ubuntu) karmic main # disabled on upgrade to quantal

---

### Post by 2F4U on 2013-05-11
Are you still using Maverick Meerkat (Ubuntu 10.10) since your sources indicate such. If yes, this release went out of support in April 2012, so it would be no wonder that the repositories do no longer exist.

---

### Post by Trig007 on 2013-05-11
no currently using 12.10

---

### Post by JRV on 2013-05-11
See my notes in bold.

```

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner   ** (Change maverick to quantal here) **
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main   ** (Change maverick to quantal here) **
deb-src http://extras.ubuntu.com/ubuntu maverick main    ** (Change maverick to quantal here) **

```

---

### Post by ibjsb4 on 2013-05-11
> deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

You need to either remove these 3 from your sources list or comment (##) them out.

---

### Post by Trig007 on 2013-05-11
All fixed & upgraded, many thanks for your help

---

### Post by ibjsb4 on 2013-05-11
Don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

