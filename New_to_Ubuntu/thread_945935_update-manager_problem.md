---
title: "update-manager problem"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by damaultz on 2008-10-12
Hi,

this message appears during updating using update manager.


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

It just happened today. There was no problem last week update. Need help.

---

### Post by jemate18 on 2008-10-12
> **damaultz said:**
> Hi,

this message appears during updating using update manager.


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

It just happened today. There was no problem last week update. Need help.

please post your /etc/apt/sources.list

---

### Post by jemate18 on 2008-10-12
try typing this

sudo apt-get check

---

### Post by damaultz on 2008-10-12
in terminal

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.



sources.list file

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb-src [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy main restricted
deb-src [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy-updates main restricted
deb-src [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy universe
deb [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy multiverse
deb [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy-security main restricted
deb-src [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy-security universe
deb [http://mirror.nttu.edu.tw/ubuntu/](http://mirror.nttu.edu.tw/ubuntu/) hardy-security multiverse
# deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/kwwii/ubuntu](http://ppa.launchpad.net/kwwii/ubuntu) hardy main
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

#ULTAMATIX REPOS START

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all





deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END
deb [http://www.tuxsoftware.com/repo/](http://www.tuxsoftware.com/repo/) hardy main
# deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main

---

### Post by Partyboi2 on 2008-10-12
Open up your /etc/apt/sources.list and change 
```
 deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") harty all
```
to
```
 deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") hardy all
```
You can make these changes by opening a terminal and
```
gksudo gedit /etc/apt/sources.list
``` make the change and save, then back in the terminal
```
sudo apt-get update
```

---

### Post by damaultz on 2008-10-13
I think the problem solved.

Thanks for the help

---

### Post by wikwanderlust on 2008-10-14
Thanks. Solved my problem too. I just want to say that I find this board amazing; Every time I think I have a major problem, I end up coming here, and the problem is fixed every time. You guys are incredible. Keep up the good work.

---

### Post by blop on 2008-10-17
Hi this helped me too..

However after an apt-get update i noticed that this line also contained the 'harty' typo and was causing an error.

"deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all"

This was one added by Ultamatix...

I suggest a find replace to make sure you get them all...

I am interested how they got there..

---

### Post by wgilbert5 on 2008-10-17
This solved the problem for me, also.  Maybe ultamatix should be taken off the system until they get it figured out.  Thanks a bunch for the solution.  Bill:):)

---

### Post by konza on 2008-10-21
Thanks from me too!  And like Wikwanderlust ya get great help from GREAT People !!!

---

### Post by markmurr on 2008-10-23
Thanks For the help... This Post Was Really Helpful. I Love Ubuntu and its wonderful help forums.

---

