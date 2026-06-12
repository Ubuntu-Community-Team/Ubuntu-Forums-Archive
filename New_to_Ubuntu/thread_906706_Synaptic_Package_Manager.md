---
title: "Synaptic Package Manager"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by clint r on 2008-08-31
Hi im a first time poster and every time ive had a problem ive come to these forums and found the answers im looking for. But this time i cant find it. Every time i try to run updates or open the package Manager i get the following message 

"E: Type '\u201cdeb' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

Any help would be very appreciated.

---

### Post by cpetercarter on 2008-08-31
System > Administration > Software Sources > Third Party Software

See if you can find on this page the item which is creating the problem. If you can identify it, uncheck it,

---

### Post by halitech on 2008-08-31
can you post the results of ```
cat /etc/apt/sources.list
```

---

### Post by clint r on 2008-08-31
here you go 

"clint@clint-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
“deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”
clint@clint-laptop:~$ 
"

---

### Post by halitech on 2008-08-31
remove the quotes from the last line or remove the line completely as it is for fiesty and you are running hardy.

```
gksu gedit /etc/apt/sources.list
```

---

### Post by drs305 on 2008-08-31
You need to delete the last line. First it has quotes, secondly it references feisty.

```

gksudo gedit +56 /etc/apt/sources.list

```

Remove the last line (gedit will open on that line) and save.
Remove: “deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”

---

### Post by halitech on 2008-08-31
> **drs305 said:**
> You need to delete the last line. First it has quotes, secondly it references feisty.

```

gksudo gedit +56 /etc/apt/sources.list

```

Remove the last line (gedit will open on that line) and save.
Remove: “deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”

cool tip, didn't know you could do a +56 (or whatever line) and have gedit open on that line. Learned something new today :D

---

### Post by clint r on 2008-08-31
thanks alot

---

