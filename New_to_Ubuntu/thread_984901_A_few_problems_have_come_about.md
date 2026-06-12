---
title: "A few problems have come about"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by b3n0 on 2008-11-17
Hey all,

Just recently I've found that a few installers constantly fail. I've just updated to Intrepid. I now find my updater will fail on some packages. Also the world of warcraft use to work fine, now the sound is all crackly. I installed wine-doors, because I was told it optimises wine for the applications you choose. I tried running that for wow but it failed. I also tried running the set up for steam through wine doors but that also failed.
Is it possible that there is some root cause to all these failures?

Thanks

---

### Post by stephanvaningen on 2008-11-17
Is it possible that you updated wow and wine via their own repositories? Did you change the software-sources of these packages to the intrepid-channel?

---

### Post by hyper_ch on 2008-11-17
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by billgoldberg on 2008-11-17
In a terminal give this command:

```
gedit /etc/apt/sources.list
```

And copy/paste the contents of that file here.

---

### Post by b3n0 on 2008-11-17
> **stephanvaningen said:**
> Is it possible that you updated wow and wine via their own repositories? Did you change the software-sources of these packages to the intrepid-channel?

I updated to the latest patch of wow through the wow downloader (like you would in windows). How do I change to the Intrepid channel?

---

### Post by b3n0 on 2008-11-18
> **billgoldberg said:**
> In a terminal give this command:

```
gedit /etc/apt/sources.list
```

And copy/paste the contents of that file here.

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
## Repository for Skype
# deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
```

---

