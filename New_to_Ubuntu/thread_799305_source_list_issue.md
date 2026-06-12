---
title: "source list issue"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by domace on 2008-05-18
I was trying to install awn for Ubuntu and added the repositories then I got the issue shown in the screen shot, so I removed it from the repositories and I still have the same issue. It also does not let me update Ubuntu. I was trying to install awn 7.10 for Ubuntu 8.04 I read that it would work but didn't. Any help would be appreciated thanks.

screen shots:

[http://i304.photobucket.com/albums/nn183/domace93/Screenshot.png](http://i304.photobucket.com/albums/nn183/domace93/Screenshot.png) 

[http://i304.photobucket.com/albums/nn183/domace93/Screenshot-update-manager.png](http://i304.photobucket.com/albums/nn183/domace93/Screenshot-update-manager.png)

---

### Post by tamoneya on 2008-05-18
post the contents of /etc/apt/sources.list.  You can get this file by hitting alt-F2 and typing ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by mkoehler on 2008-05-18
Can you post the content of /etc/apt/sources.list for us?

---

### Post by domace on 2008-05-19
/etc/apt/sources.list




t# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by PmDematagoda on 2008-05-19
Open the sources list for editing with:-
```
gksudo gedit /etc/apt/sources.list
```
and remove the very first line(since it is for the 7.10 install CD) and then save the file, once that is done do:-
```
sudo apt-get update
```

That should fix the problem.

---

### Post by dichtbijzee on 2008-05-19
Please remove the "t" at the beginning of the file.

and then it should function again.

---

### Post by domace on 2008-05-19
thanks everything seems to be working fine now, I can't believe I didn't know how to do this...lol

---

