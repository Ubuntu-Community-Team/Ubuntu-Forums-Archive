---
title: "sudo apt-file update"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-06-13
The command sudo apt-file update asks me to put in the Ubuntu cd rom.
After doing so i execute the command again and the response is this:

```
mehrzad@mehrzad-laptop:~/mount$ sudo apt-file update
Put CDROM labeled [Ubuntu_8.04__Hardy_Heron__-_Release_i386_(20080423)] in the cdrom device
read: 1: arg count
mount: block device /dev/scd0 is write-protected, mounting read-only
cp: cannot stat `/cdrom/dists/hardy/Contents-i386.gz': No such file or directory
Put CDROM labeled [Ubuntu_7.10__Gutsy_Gibbon__-_Release_i386_(20071016)] in the cdrom device
read: 1: arg count
mount: block device /dev/scd0 is write-protected, mounting read-only
cp: cannot stat `/cdrom/dists/gutsy/Contents-i386.gz': No such file or directory
  

```

What should i do.

---

### Post by milton1 on 2008-06-13
looks like apt is looking for conflicting cdrom sources. Can you post the contents of your /etc/apt/sources.list file?

---

### Post by drs305 on 2008-06-13
Disable the cdrom input in synaptic. Synaptic, Settings, Repositories, untick the cdrom in the lower window. You will no longer be asked to insert the cd whenever you want to update something.

---

### Post by 7raTEYdCql on 2008-06-13
```

mehrzad@mehrzad-laptop:~/mount$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets


```

---

### Post by drs305 on 2008-06-13
Alternatively to my earlier post, (which I still recommend), you can comment out the two references to the cdroms in your /etc/apt/sources.list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak1
gksudo gedit /etc/apt/sources.list
```

Change this:
```
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

To this:
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

---

### Post by milton1 on 2008-06-13
As I suspected, these lines: 
```
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```
indicate that apt is looking for the cdrom's from two different versions. Your souces.list needs some help. What version of ubuntu are you using, gutsy, or hardy?

---

### Post by 7raTEYdCql on 2008-06-13
I am using Gutsy gibbon but dont have the cd with me. I have the hardy cd with me.

---

### Post by milton1 on 2008-06-13
OK, then drs305's advice for commenting out the cdrom entries in your sources.list should do the trick.

---

### Post by liviubero on 2008-07-25
I have the same problem. I am using Hardy and there is no cdrom entry in my /etc/apt/sources.list
The output is this one:
```
liviu@lorien:~/Desktop$ sudo apt-file update 
Can't get http://archive.canonical.com/ubuntu/dists/hardy/Contents-i386.gz
Can't get http://ppa.launchpad.net/superm1/ubuntu/dists/hardy/Contents-i386.gz
```
With or without cdrom it doesn't work.

---

