---
title: "Adding ubuntu repositories"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-06-22
Hey everyone,

I was wondering how to add the Ubuntu repos to my Xandros install.. I know I'm supposed to add the locations to /etc/apt/sources.list but I don't know the locations or whatever.. I've only done this a few times and usually I'm told what lines to add.

---

### Post by LaRoza on 2008-06-22
> **mishathegoat said:**
> Hey everyone,

I was wondering how to add the Ubuntu repos to my Xandros install.. I know I'm supposed to add the locations to /etc/apt/sources.list but I don't know the locations or whatever.. I've only done this a few times and usually I'm told what lines to add.

Here's mine, don't know which ones you want.

```

~$cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by Oldsoldier2003 on 2008-06-22
> **mishathegoat said:**
> Hey everyone,

I was wondering how to add the Ubuntu repos to my Xandros install.. I know I'm supposed to add the locations to /etc/apt/sources.list but I don't know the locations or whatever.. I've only done this a few times and usually I'm told what lines to add.
Try this link in the Ubuntu Community Documentation Wiki :
[uhelp]community/Repositories/CommandLine[/uhelp]

Its pretty comprehensive and will give you a good understanding of the process.

---

### Post by nhandler on 2008-06-22
Here are the ones you probably are interested in:

#Main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

#Updates
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

#Universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

#Universe Updates
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

#Multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

#Multiverse Updates
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

#Backports
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

#Security Main and Restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted

#Security Universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe

#Security Multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse

Those repositories should be what you want. These are the hardy repositories.

---

### Post by mishathegoat on 2008-06-23
Some of theme were successfully added but I'm getting some sort of public key errors... any ideas?

---

