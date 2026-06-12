---
title: "add/remove programs out of date"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by zero777zero on 2008-08-30
there are some really old versions in the "Add/Remove Applications"

why is this?

hardy heron, auto updates on

---

### Post by tamoneya on 2008-08-30
can you give some examples?  It may be that the package maintainer has forgotten but that is rarely the case from my what I have seen.  Typically they do a very good job keeping things up to date.  Unless there is some serious flaw in the current version they typically get updated promptly.  Examples would help though.

---

### Post by zero777zero on 2008-08-30
i guess my question was more geared towards who is supposed to maintain them, ubuntu or the individual program developers. some of the ones i noticed before have been updated since, but i did download a program the other day which said "this program is a very old version" or something of the like
these ones arent drastic, although some are a few months old
pidgin 2.4.1 current 2.5
audacious 1.5 current 1.5.1
the gimp 2.4.5 current 2.4.7
transmission 1.06 current 1.3.3
ophcrack 2.4.1 current 3.0.1
filezilla 3.0.7.1 current 3.1.2
GParted 0.3.5 current 0.3.8

the only one that i looked at that was up to date is wine. i assume this is the responsibility of the individual software developers, but if it is ubuntus reponsibility, they need to get on it!

also, who adds programs to the add/remove list? i would like to see some playstation emus added to relieve the trouble i'm having installing them (after many many tries)

---

### Post by tamoneya on 2008-08-30
for the most part program updates that add new features or depreciate old features are only done when on the number releases.  2.4.1 was put in hardy and 2.5 will be put in intrepid for pidgin. Update manager will add in updates that are bug fixes.  The reasoning behind this applies more to lower level applications in the OS because the developers dont want to break stuff.  It is hard though to determine where to draw the line as to what is more of a system level program that shouldnt be upgraded for new features and what is a more top level program.  If you want you can install the new versions by hand or wait for 8.10.  Also sometimes ubuntu developers intentionally hold back on some versions if they think it doesnt benefit users and will only cause problems and bugs in the OS.

---

### Post by zero777zero on 2008-08-30
ok that makes sense, thanks for the info

---

### Post by Oldsoldier2003 on 2008-08-31
see [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) for more info

---

### Post by jdorenbush on 2008-09-12
I was just going to ask this question because I noticed that my Banshee music player was out of date. I installed it via Add/Remove. Then I went to the Banshee website and noticed that a much newer version was out, but I had to add third-party sources and everything to get the up to date version. This also happened with Transmission. I am sure there is more software I have that is out of date. :( Can I assume that Add/Remove isn't the best way to install software? Should I be going to the developer sites and following install instructions every time I need new software, in case I need to install sources. Is there an easier way to do this? A better to monitor software updates to confirm that I have the latest stuff?

> **tamoneya said:**
> If you want you can install the new versions by hand or wait for 8.10.

This is something that I have been curious about for sometime. Hopefully this doesn't completely derail the thread. Hardy is the first Ubuntu OS I have used. Does Ubuntu update itself to the latest version, e.g. Intrepid Ibex or is it like reinstalling a whole new operating system, e.g. Windows XP to Windows Vista?

---

### Post by Sef on 2008-09-13
Moved to absolute beginners.

---

### Post by mcduck on 2008-09-13
By the way, [http://www.getdeb.net/]("http://www.getdeb.net/") is a nice place to get more up-to-date packages.. And remember to enable the backports repository. ;)

jdorenbush: when the new Ubuntu version is released, the update manager will tell you about it and offer you an option to upgrade to the latest Ubuntu version.

Most of the time this works fine, but some people prefer doing fresh installs (which is quite easy to do as well, as long as you keep your old home directory safe all your personal settings will stay.

Also, you when upgrading you can't jump over versions, for example you can't upgrade from 7.10 to 8.10, you'd need to go from 7.10 to 8.04 and then 8.10. So in that case a fresh install directly to 8.10 would be easier.

---

### Post by jmfa59 on 2008-09-13
I had the same problem and I posted it in this great forum, Igot the answer in this thread which worked like charm
[http://ubuntuforums.org/showthread.php?t=608848](http://ubuntuforums.org/showthread.php?t=608848)
I hope it will help you

---

### Post by jdorenbush on 2008-09-13
> **jmfa59 said:**
> I had the same problem and I posted it in this great forum, Igot the answer in this thread which worked like charm
[http://ubuntuforums.org/showthread.php?t=608848](http://ubuntuforums.org/showthread.php?t=608848)
I hope it will help you

I tried that. I don't know if it helped. 

This is what my sources.list looked like:
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu-rocks.org/ubuntu/ hardy main restricted multiverse
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates main restricted multiverse
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy universe
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy universe
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates universe

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
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main universe multiverse
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-proposed restricted main universe multiverse
# deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/bortis/ubuntu hardy main
deb-src http://ppa.launchpad.net/bortis/ubuntu hardy main
deb http://ppa.launchpad.net/banshee-team/ubuntu/ hardy main
```

I removed all the #'s towards the bottom of the list.

---

