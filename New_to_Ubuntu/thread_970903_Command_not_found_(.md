---
title: "Command not found :("
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Linuxidiot on 2008-11-04
Hello im trying to install Moblock on my ubuntu , so when i went to the howto page it had easy looking instructions but when i got to the part that says.....Add specific repository for release

You have to add the repository sources to your /etc/apt/sources.list:

    *

      gksu gedit /etc/apt/sources.list

In Kubuntu, replace gksu with kdesu.

Add the two lines for your specific release (i.e. Ubuntu 7.10):

Ubuntu ("Intrepid Ibex") 32-bit and 64-bit

    *

      deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main
      deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main.....

I get an error in my command line that says bash: deb: command not found
What am i doing wrong???

---

### Post by Ek0nomik on 2008-11-04
```
deb http://moblock-deb.sourceforge.net/debian intrepid main
deb-src http://moblock-deb.sourceforge.net/debian intrepid main.....
```

Those lines are supposed to be pasted into your sources.list file.

So, gedit your sources.list file, and add those two sources to the file.

---

### Post by Linuxidiot on 2008-11-04
Thanks ill give it a quick try :)....when i get into Gedit it gives me a list of Https...where would i put it...just at the bottom of the page or something....it looks like # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release Candidate i386 (20081022)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by Sarmacid on 2008-11-04
Put it wherever you want. I usually put repositories added this way on top, wrapped around comments to clarify where I got them. Comments are made by putting a # at the start of the line.

---

### Post by Linuxidiot on 2008-11-04
Thank you much:)

---

### Post by taurus on 2008-11-04
> **Sarmacid said:**
> Put it wherever you want. I usually put repositories added this way on top, wrapped around comments to clarify where I got them. Comments are made by putting a # at the start of the line.

Personally, I would add them to the bottom, after all the standard/default repos.

---

