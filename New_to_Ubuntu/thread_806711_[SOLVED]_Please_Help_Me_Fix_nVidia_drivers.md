---
title: "[SOLVED] Please Help Me Fix: nVidia drivers"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-05-25
Hi, 

I have been building up a "to fix" list for my computer. The second problem I would like to fix is my nVidia drivers. 

In my posts [here]("http://ubuntuforums.org/showthread.php?t=770543"), [here]("http://ubuntuforums.org/showthread.php?t=758292") and [here]("http://ubuntuforums.org/showthread.php?t=692683"), I describe problems viewing video (where crazy patterns appear) and problems with Ubuntu freezing up. In one of the posts, somebody suggests running glxgears - the test results were very bad and my whole system froze up when I ran it. 

All of these problems seem to be related to my graphics card because when I disable the drivers (and hence compiz) all of the problems have stopped. Ubuntu never freezes (weey heyy!) and I have no problems watching vids now too.

However, not having the appropriate graphics card driver makes my display suck. I would like to re-enable it but without encountering all those problems. 

Thanks for any help!

J

---

### Post by shifty_powers on 2008-05-25
did you try envy?

---

### Post by Jimmy9pints on 2008-05-25
Envy? What's that? Tried to look it up but didn't get many useful results.

---

### Post by shifty_powers on 2008-05-25
```
sudo apt-get install envyng-gtk
```

then go applications>system tools>envyng

it is a tool to identify your graphics card and install the right drivers for it...

---

### Post by Jimmy9pints on 2008-05-25
Uh oh, I got this

```
james@james-desktop:~$ sudo apt-get install envyng-gtk
[sudo] password for james:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk
james@james-desktop:~$ 

```

What's going on?

---

### Post by shifty_powers on 2008-05-25
heh, ok.

post the output of

```
sudo gedit /etc/apt/sources.list
```

---

### Post by shifty_powers on 2008-05-25
also

[http://packages.ubuntu.com/hardy/envyng-gtk](http://packages.ubuntu.com/hardy/envyng-gtk)

contains the deb file for envyng, and it's dependencies....

---

### Post by Jimmy9pints on 2008-05-26
the output of sudo gedit /etc/apt/sources.list is:


```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://cn.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://cn.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cn.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://cn.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://cn.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://cn.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://cn.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://cn.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://cn.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.canonical.com/ubuntu feisty partner
deb http://archive.canonical.com/ubuntu feisty-commercial main
deb http://packages.medibuntu.org/ gutsy free non-free

deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main

deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 main -
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 main
```

---

### Post by Nepherte on 2008-05-26
Envy is not available in the repositories for gutsy. You can download the deb file for gutsy from the official envy website: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
(be sure you download the envy-legacy version)

---

### Post by Jimmy9pints on 2008-05-31
Believe it or not 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

is blocked from China. Alberto must have done something to offend the establishment here.

---

### Post by spiderbatdad on 2008-06-01
```
sudo apt-get install nvidia-xconfig
```???

---

### Post by Jimmy9pints on 2008-06-01
What does that do, sorry?

---

