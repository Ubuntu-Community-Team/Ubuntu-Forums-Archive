---
title: "unable to install realplayer"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-05-23
i just hate it when things dont work, especially when you follow the instructions to the dot!!!! 

here is my sources.list file:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu dapper-commercial main


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.canonical.com/ubuntu dapper-commercial main

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse restricted universe main
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## zman0900's PPA
deb http://ppa.launchpad.net/zman0900/ubuntu hardy main
deb-src http://ppa.launchpad.net/zman0900/ubuntu hardy main
```


as you can see, i have the following line:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

twice! yet the flipping crappy terminal gives me an error whenever i type:

```
sudo apt-get install realplay
```

the error is:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package realplay

```


why? 

sigh...

---

### Post by Bodsda on 2008-05-23
that would be because its called *realplayer*

make sure you have the multiverse repo enabled then type

```
 sudo apt-get install realplayer 
```

Remember the tab key is your best friend, press tab while doing something in a terminal and it will automatically write what you need (if youve typed enough letters already)

---

### Post by Maestro23 on 2008-05-23
Or Download the latest version: [http://www.real.com/linux](http://www.real.com/linux)

Download to Desktop and install.

> cd Desktop

sudo chmod +x RealPlayer11GOLD.bin

sudo ./RealPlayer11GOLD.bin


---

### Post by logos34 on 2008-05-23
I see that the 11 version now has the ability to pause and ff/rew live streams.  Finally.  Any other new features I should be aware of (beside multichannel capability which I can't use)?  Maybe I'll switch back (using Mplayer/mplayer mozilla plugin now).

---

### Post by hotweiss on 2008-05-23
> **Maestro23 said:**
> Or Download the latest version: [http://www.real.com/linux](http://www.real.com/linux)

Download to Desktop and install.

I just converted the RealPlayer 11 rpm to a deb using alien.

---

### Post by Bodsda on 2008-05-23
i find it quite annoying that the windows version is brilliant and the linux version is ** crap **

---

### Post by jrusso2 on 2008-05-23
> **logos34 said:**
> I see that the 11 version now has the ability to pause and ff/rew live streams.  Finally.  Any other new features I should be aware of (beside multichannel capability which I can't use)?  Maybe I'll switch back (using Mplayer/mplayer mozilla plugin now).

I read Real Player 11 will now play Windows streams which would give American Linux user a "legal" way to play Windows streams on Linux.

---

