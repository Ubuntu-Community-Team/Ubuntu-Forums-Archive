---
title: "[SOLVED] This is an interesting error i got this morning"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Anthony Fox on 2008-07-11
i popped on this morning and had an unusual error i am still pretty green to linux and have no clue where to even start to try and fix this


E:Malformed line 58 in source list /etc/apt/sources.list (url parse)
E:the list of sources could not be read
 
any feed back is greatly appreciated

---

### Post by fatality_uk on 2008-07-11
Open a terminal and type:
> gedit /etc/apt/sources.list
And post the results.

---

### Post by Anthony Fox on 2008-07-11
it came back with
 deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main

---

### Post by sharks on 2008-07-11
do u get this error while trying to update or upgrade?
sudo apt-get update
sudo apt-get upgrade

---

### Post by Anthony Fox on 2008-07-11
i got it while trying to run update manager

---

### Post by hyper_ch on 2008-07-11
when posting any kind of config or output from the cli use

[noparse]```

```[/noparse]

brackets around it so it can easier be read.

---

### Post by sharks on 2008-07-11
post the error from terminal when using this command:
sudo apt-get update
sudo apt-get upgrade

---

### Post by Anthony Fox on 2008-07-11
it came back with
E: Malformed line 58 in source list /etc/apt/sources.list (URI parse)

---

### Post by rxtx on 2008-07-11
Comment out the last line of the sources file (which is in fact 58 ).

```
sudo nano /etc/apt/sources.list
```

Scroll down to the last line, add two hash/pound signs "#" in front of the last line so it reads:

"## deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main"

CTRL + X to exit, confirm your save.

Try your apt-get commands again :)

---

### Post by philinux on 2008-07-11
Comment out the last line with a #

---

### Post by Anthony Fox on 2008-07-11
still getting the same thing 
E: Malformed line 58 in source list /etc/apt/sources.list (URI parse)

---

### Post by rxtx on 2008-07-11
Can you post your modified sources file for us? :)

---

### Post by Anthony Fox on 2008-07-11
the single hash mark got it i didn't get the error this time

---

### Post by Anthony Fox on 2008-07-11
thanks to all for your time it is up and good

---

### Post by philinux on 2008-07-11
I'd just delete the line and be rid.

---

### Post by sharks on 2008-07-11
if ur question is solved please mark the thread solved from thread tools.

---

### Post by ChameleonDave on 2008-07-11
> **hyper_ch said:**
> when posting any kind of config or output from the cli use

[noparse]```

```[/noparse]

brackets around it so it can easier be read.

You're getting a medal!  :KS

[noparse][noparse][/noparse][/noparse] is fantastic!  I can finally tell newbies how to post code legibly!! :guitar:

---

