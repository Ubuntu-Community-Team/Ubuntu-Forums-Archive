---
title: "[SOLVED] got a problem on Visual Effects (Appearance Preferences)"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by rhanex on 2008-06-12
**Can't activate the desktop effects, heres some shots i took.**

---

### Post by iaculallad on 2008-06-12
Try posting your /etc/apt/sources.list

```
cat /etc/apt/sources.list
```

---

### Post by rhanex on 2008-06-13
> **iaculallad said:**
> Try posting your /etc/apt/sources.list

```
cat /etc/apt/sources.list
```


**here it is..**
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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

---

### Post by alienexplorers on 2008-06-14
Do you have your drivers for your graphic card loaded.  If not, then use ENVY if you have a nvidia or ATI card to load your drivers.  Once loaded reboot and then try to load compiz.

---

### Post by Ub1476 on 2008-06-14
Make sure all sources is checked in System>Administration>Software Sources.

Then update your system, with Synaptic or CLI:

```
sudo apt-get update
sudo apt-get upgrade
```

Try to enable the visual effects in Preferences>Appearance.

If "desktop effects can't be enabled", check Hardware Drivers for a driver for your graphic card.

You can also post your graphic card. It's displayed with this command:

```
lspci | grep VGA
```

However, an update sometimes do wonders. :)

---

### Post by rhanex on 2008-06-14
it worked! After i successfully install and run Envy then update and upgrade, I'm able now to use compiz.
**thanks guys**!!

 Upgrade went smoothly however, the Update leave some errors :(
and the "lspci | grep vga" command seems does not work on me (nothing happens after i hit enter)

Anyway heres some errors from my last Update:

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

.....I'm still good?            ....am i:confused:

---

### Post by Victormd on 2008-06-14
Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and under the Ubuntu Software tab, un-check the "Cdrom with Ubuntu 8.04 'Hardy Heron' option and your errors should go away... :)

The previous command should be:
```
lspci | grep VGA
```
(capitalized VGA)
Also, to check if you've got proper rendering, it's better to use
```
glxinfo | grep rendering
```
and if you do, you'll get an output like this:
> direct rendering: Yes

---

### Post by rhanex on 2008-06-14
thanks bro, I got it now ](*,)kinda noob tho..](*,)

rhanex@x-zodia:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)

and 

rhanex@x-zodia:~$ glxinfo | grep rendering
direct rendering: Yes

yay, i have a verry long way to learn my new OS.. :):razz:

---

### Post by Victormd on 2008-06-14
Great!
If you need anything else, just let us know...

BTW, if this solved your problem, mark the thread as solved... :)

---

