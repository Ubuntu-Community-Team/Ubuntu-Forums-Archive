---
title: "Is this a bug ...."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by mvashi on 2008-04-23
While updating I get this message

E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I wonder if this is generated because the package manager cannot connect to the servers.
Tried different servers with the same result

---

### Post by PeterJS on 2008-04-23
What's on line 5 of your sources list?

---

### Post by myusername on 2008-04-23
you probably have a broken package

---

### Post by overdrank on 2008-04-23
> **mvashi said:**
> While updating I get this message

E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I wonder if this is generated because the package manager cannot connect to the servers.
Tried different servers with the same result
HI and as suggested by PeterJS you can use this command in the terminal
```
gksudo gedit /etc/apt/sources.list
```
To view and edit your list and look for a error on line 5. You can post here and we can help

---

### Post by mvashi on 2008-04-23
Well this is my souces.list
 I am not sure which one os line 5 . I was not sure if I were to ignore lines starting with # as a comment .

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb Canada hardy main restricted
deb-src Canada hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb Canada hardy-updates main restricted
deb-src Canada hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb Canada hardy universe
deb-src Canada hardy universe
deb Canada hardy-updates universe
deb-src Canada hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb Canada hardy multiverse
deb-src Canada hardy multiverse
deb Canada hardy-updates multiverse
deb-src Canada hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb Canada hardy-security main restricted
deb-src Canada hardy-security main restricted
deb Canada hardy-security universe
deb-src Canada hardy-security universe
deb Canada hardy-security multiverse
deb-src Canada hardy-security multiverse
deb [http://hydr0g3n.free.fr/qbittorrent/hardy/](http://hydr0g3n.free.fr/qbittorrent/hardy/) ./
deb-src [http://hydr0g3n.free.fr/qbittorrent/hardy/](http://hydr0g3n.free.fr/qbittorrent/hardy/) ./

---

### Post by PeterJS on 2008-04-23
> **mvashi said:**
> Well this is my souces.list
 I am not sure which one os line 5 . I was not sure if I were to ignore lines starting with # as a comment .

```

1)# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
2)# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
3)# newer versions of the distribution.
4)
5)deb Canada hardy main restricted

```

There we go, "Canada" is most assuredly not a valid url. If you go to System > Administration > Software sources you can change which mirror you're using.

---

### Post by mvashi on 2008-04-23
References to "Canada" were in third party software
unchecked all , but I cannot select the server for Canada
Well anyways , I am currently installing the updates
Thank you

---

