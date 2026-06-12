---
title: "sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192"
date: 2017-11-04
forum: New to Ubuntu
---

### Post by samsons92 on 2017-11-04
Hi,

Getting the below error messages when running sudo apt-get update command.


Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_IN               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages [13.9 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages 
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages [4,953 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en [2,564 B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en [3,542 B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en [110 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release [11.9 kB]                      
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages [1,348 kB]          
Fetched 1,573 kB in 2min 5s (12.6 kB/s)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release](http://archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


_**Sources.list entry**_


# deb cdrom:[Ubuntu 14.04.5 LTS _Trusty Tahr_ - Release i386 (20160803)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

---

### Post by oldos2er on 2017-11-04
To fix the hash sum mismatch error, try ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt update
```

---

### Post by samsons92 on 2017-11-05
@oldos2er, Tried the steps.. But no luck. Now getting the below error.


Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en [369 kB]  
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en [2,564 B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en [3,542 B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en [110 kB]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages [14 B]              
Fetched 3,870 kB in 9s (393 kB/s)                                              
W:  Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release](http://archive.ubuntu.com/ubuntu/dists/trusty/Release)   Unable to find expected entry 'restricted/binary-i386/Packages' in  Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by oldos2er on 2017-11-05
Rerun those commands again; they should've worked. Nothing in your sources.list is jumping out at me as wrong, but you could also try going to [https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/) and generating a new list.

Why did you title your thread with something that has nothing to do with your problem?

---

