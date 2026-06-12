---
title: "Getting gedit on new install of xubuntu"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2008-09-09
Hi
I'm looking for a little guidance about how to get gedit for xubuntu.  I've got a fresh install & am very new to linux, so any help is appreciated.  Thanks

---

### Post by Elfy on 2008-09-09
You can run this in a terminal

```
sudo apt-get install gedit
```

It will ask for your password - but it won't appear as you type, it is there though.

---

### Post by beetlejuice_masterson on 2008-09-09
I get a "couldn't find package gedit" error... I am not connected to the net--is this the problem?

---

### Post by whitethorn on 2008-09-09
yes you have to be connected to the net.

---

### Post by Elfy on 2008-09-09
YEs probably :)

How are your sources set up - not too sure about menu options in xubuntu so run this in a terminal

```
cat /etc/apt/sources.list
```

Then copy and paste it here - please put it inside code tags - first at beginning, second at end

[noparse]first```
 and second
```[/noparse]

---

### Post by beetlejuice_masterson on 2008-09-09
```

# 
# deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main multiverse restricted universe

#deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main multiverse restricted universe
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

### Post by Elfy on 2008-09-09
aaah I don't actually think this will work, pretty sure that gedit isn't on the xubuntu cdrom, but you can try - open the file to edit it ```
gksudo mousepad /etc/apt/sources.list
``` remove # from the cdrom line > # deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main multiverse restricted universe

save and close the file.

Make sure you have the cd in the drive and run ```
sudo apt-get update
``` it will complain about the rest of the sources being unavailable as you have no net, then try to run the install command again.

But you can use mousepad instead of gedit...

---

