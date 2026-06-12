---
title: "Error Messages, completely lost on how to solve."
date: 2015-04-30
forum: New to Ubuntu
---

### Post by weirdointheback on 2015-04-30
Hello all, I just recently installed Xubuntu on my PC and I seem to have met with an error already. I don't know exactly what to do about it.

E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I'm not sure how I am to fix this. Been looking around the net for some answers but none have been particularly helpful.

---

### Post by deadflowr on 2015-05-01
Post your sources.list
copy and paste the output of this command
```
cat /etc/apt/sources.list
```
and then copy the output into this thread.

(Please use code tags
Look here on how-to do that
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168))

Then we can see what line 56 says wrong.
It's usually a quick fix.

---

### Post by weirdointheback on 2015-05-01
Okay, thank you.

Here's how the output looks.

```

# deb cdrom:[Xubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://bz.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://bz.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://bz.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://bz.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://bz.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://bz.archive.ubuntu.com/ubuntu/ trusty universe
deb http://bz.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://bz.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://bz.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://bz.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://bz.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://bz.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://bz.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://bz.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb http://archive.canonical.com/trusty partner
# deb-src http://archive.canonical.com/trusty partner
deb http://archive.canonical.com/ trusty partner
# deb-src http://archive.canonical.com/ trusty partner
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

---

### Post by weirdointheback on 2015-05-01
I actually fixed it just now haha. I just needed to add a space. Sorry for the trouble

---

