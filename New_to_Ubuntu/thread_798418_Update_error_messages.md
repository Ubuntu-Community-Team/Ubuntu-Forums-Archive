---
title: "Update error messages"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Peterfc on 2008-05-18
Hi All

I updated to 8.4 on release date and all went well. For a few days i have not been able to update due to error messages . I am sorry but i do not understand what to do.  Also for some reason i am now on KDE instead of Gnome???

Could anybody help please?


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Version 0.1.2: 

  * usr/share/recovery-mode/options/dpkg:
    - add recovery mode for package failure (LP: #228200)


Version 0.1.1: 

  * usr/share/recovery-mode/options/root:
    - use /sbin/sulogin to get a shell (LP: #220986)

---

### Post by forestpixie on 2008-05-18
First - the dpkg error try this- if it gives an error post it here

```
sudo dpkg --configure -a
```

If after that you still get Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ ...
```
cat /etc/apt/sources.list
```
and postit here

---

### Post by Peterfc on 2008-05-18
Hi Forestpixie

Sorry to be a pain. i have tried both answers and rebooted after each one still a problem listed below. One good thing Gnome is back. 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by forestpixie on 2008-05-18
First - which version are you using, can you open a terminal and do

```
cat /etc/apt/sources.list
```

---

### Post by Peterfc on 2008-05-18
Hi Forestpixie

I can get into a terminal and cat /etc/apt/sources.list i get a list and then it goes back to the promt.

---

### Post by forestpixie on 2008-05-18
Could you post it then - I did ask in my first post :)

also which version of ubuntu are you using

---

### Post by Peterfc on 2008-05-18
Sorry missed the post for the list. 


peter@peter:~$ cd Desktop
peter@peter:~/Desktop$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates main
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy multiverse
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security main
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security main
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security multiverse
peter@peter:~/Desktop$

---

### Post by forestpixie on 2008-05-18
> Sorry missed the post for the list.No matter - I asked twice what version you were using and you said that in the original post :) 

Re - the kde thing - are you sure that you don't have both - on login - bottom left change session - see what's there.

Open the file to edit it - I've put red where to change, this command for kde - change to gksudo gedit for gnome, if you don't want sources comment them out as well.

```
kdesu kate /etc/apt/sources.list
```

> [COLOR="Red"]#[/COLOR]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates main
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy multiverse
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="#ff0000"]#[/COLOR]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
[COLOR="#ff0000"]#[/COLOR]deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security main
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security main
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security multiverse

Close and save then try

```
sudo apt-get update
```

Post back with problems

---

### Post by Peterfc on 2008-05-18
Hi forestpixie

Looked in  sessions and only now showing Gnome  Hope that's ok.
Tried next  kdesu kate /etc/apt/sources.list and get a message below.

peter@peter:~$ ICE default IO error handler doing an exit(), pid = 8491, errno = 11

---

### Post by Sef on 2008-05-18
If you are on Kubuntu, then this code is incorrect:

```
sudo dpkg --configure -a
```.

The correct code would be

```
kdesu dpkg --configure -a
```

Once all is well,  read Psychocat's [Install Ubuntu]("http://www.psychocats.net/ubuntu/gnome") to install ubuntu and [Install KDE]("http://www.psychocats.net/ubuntu/kde") to remove Kubuntu.

---

### Post by forestpixie on 2008-05-18
Edit the file with the gksudo gedit command then, 

```
gksudo gedit /etc/apt/sources.list
```

@sef - not sure what dpkg -configure has to do with editing the sources.list?

---

### Post by Peterfc on 2008-05-18
Hi All

Thanks you all for what you have helped me get done today. Ubuntu is well worth using even with minor problems. I am 59 and it's not as easy to do but thanks.

---

