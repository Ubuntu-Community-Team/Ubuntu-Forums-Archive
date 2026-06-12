---
title: "problem with update manager"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by zabergan on 2008-11-26
Hi

I have a problem my update manager - every time I open I get this error message:
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 54 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read.'

What should I do?

---

### Post by bruce89 on 2008-11-26
Post the file /etc/apt/sources.list, especially line 54.

---

### Post by zabergan on 2008-11-26
I got this reply when I posted the  /etc/apt/sources.list

bash: /etc/apt/sources.list: Permission denied

---

### Post by ibizatunes on 2008-11-26
type sudo gedit /etc/apt/sources.list

---

### Post by zabergan on 2008-11-26
> **ibizatunes said:**
> type sudo gedit /etc/apt/sources.list

Ok here's what I got

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

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


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb ubuntu 8.10

---

### Post by binbash on 2008-11-26
delete this line : deb ubuntu 8.10

---

### Post by zabergan on 2008-11-26
> **binbash said:**
> delete this line : deb ubuntu 8.10

Thanx - working fine now:)

---

