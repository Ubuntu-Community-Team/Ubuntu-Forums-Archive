---
title: "Check for updates problem"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by Charitarth on 2013-05-16
Hello guys,

I am relatively new to command line working of Linux. I have ubuntu 12.04. I havent updated my OS for long time so when I, today trough Update manager, started cheking for updates i received this message 

W:Failed to fetch cdrom://Ubuntu 12.04 _Precise Pangolin_ - Release i386 (20120802)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.04 _Precise Pangolin_ - Release i386 (20120802)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Can anyone help me resolve these problems ? 

Thanks 

Charitarth

---

### Post by dino99 on 2013-05-16
please post the output of:

cat /etc/apt/sources.list

note: run that command inside a terminal (ctrl+alt+t)

---

### Post by Charitarth on 2013-05-16
Hi ! Thanks for replying. 

here is the output 

deb cdrom:[Ubuntu 12.04 _Precise Pangolin_ - Release i386 (20120802)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main




I hope you can workout something out of it :) 

Thanks

Charitarth

---

### Post by plucky on 2013-05-16
```
deb cdrom:[Ubuntu 12.04 _Precise Pangolin_ - Release i386 (20120802)]/ precise main restricted

```

You need to edit the file and put a # in front of the line above.

```
gksudo gedit /etc/apt/sources.list
```

That will stop the update manager looking for your install CDrom.

Then run ```
sudo apt-get update
```

Good Luck

---

### Post by Charitarth on 2013-05-16
Thanks a lot plucky ! 

It has worked flawless ! 

I am loving ubuntu more now :)

---

