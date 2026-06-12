---
title: "Ubuntu 14.04 : SUMO installation libraries problem"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by xptional on 2014-06-21
Dears, 
I got headache to solve the below mentioned problem. I search this way and that way on internet but could not to target point. Unfortunately now im on ubuntu 14.04 LTS because 10.04 LTS crashed sudden.

```
sudo apt-get install sumo
```
> Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 sumo : Depends: libgdal1 (>= 1.9.0) but it is not installable
E: Unable to correct problems, you have held broken packages.


I followed the procedure as, 

```
[COLOR=#000000][FONT=monospace]sudo add-apt-repository ppa:sumo/stable
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo apt-get update [/FONT][/COLOR][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo apt-get install sumo sumo-tools sumo-doc[/FONT][/COLOR]
```

Then following the below link, and installing libraries one by one. 
[http://packages.ubuntu.com/trusty/science/sumo](http://packages.ubuntu.com/trusty/science/sumo)

Anyhow below works well.
```
sudo apt-get install sumo-tools
sudo apt-get install sumo-doc
```
I tried the below procedure but failed. Same error happen. But this procedure helped me when I had 10.04 LTS.
[http://alibalador.blogspot.fr/2013/03/installing-sumo-with-gui-on-ubuntu-1204.html](http://alibalador.blogspot.fr/2013/03/installing-sumo-with-gui-on-ubuntu-1204.html)

Please respond me how to solve it. Thank you so much.

Some outputs that can be concerned or help to solve  or analyse the problem
```
**sudo apt-get -f install**
```
> sudo apt-get -f install
[sudo] password for khan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```
**gksudo gedit /etc/apt/sources.list**
```
> # deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricteddeb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted #Added by software-properties


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty restricted main multiverse universe #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-updates restricted main multiverse universe #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse #Added by software-properties


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
```
[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list[/FONT][/COLOR]
```
> # deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricteddeb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted #Added by software-properties


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty restricted main multiverse universe #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-updates restricted main multiverse universe #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse #Added by software-properties


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
```
ls -l /etc/apt/sources.list.d
```
> total 80-rw-r--r-- 1 root root  56 juin  21 11:29 getdeb.list
-rw-r--r-- 1 root root  56 juin  21 11:29 getdeb.list.save
-rw-r--r-- 1 root root 138 juin  21 11:29 gnome3-team-gnome3-trusty.list
-rw-r--r-- 1 root root 138 juin  21 11:29 gnome3-team-gnome3-trusty.list.save
-rw-r--r-- 1 root root 176 juin  21 11:29 google-chrome.list
-rw-r--r-- 1 root root 176 juin  21 11:29 google-chrome.list.save
-rw-r--r-- 1 root root 112 juin  21 11:29 libdvdcss.list
-rw-r--r-- 1 root root 112 juin  21 11:29 libdvdcss.list.save
-rw-r--r-- 1 root root 224 juin  21 11:29 otto-kesselgulasch-gimp-trusty.list
-rw-r--r-- 1 root root 224 juin  21 11:29 otto-kesselgulasch-gimp-trusty.list.save
-rw-r--r-- 1 root root  57 juin  21 11:29 playdeb.list
-rw-r--r-- 1 root root  57 juin  21 11:29 playdeb.list.save
-rw-r--r-- 1 root root 124 juin  21 11:29 sumo-stable-trusty.list
-rw-r--r-- 1 root root 126 juin  21 11:29 sumo-stable-trusty.list.save
-rw-r--r-- 1 root root 144 juin  21 11:29 videolan-stable-daily-trusty.list
-rw-r--r-- 1 root root 144 juin  21 11:29 videolan-stable-daily-trusty.list.save
-rw-r--r-- 1 root root 134 juin  21 11:29 webupd8team-java-trusty.list
-rw-r--r-- 1 root root 134 juin  21 11:29 webupd8team-java-trusty.list.save
-rw-r--r-- 1 root root 152 juin  21 11:29 webupd8team-y-ppa-manager-trusty.list
-rw-r--r-- 1 root root 152 juin  21 11:29 webupd8team-y-ppa-manager-trusty.list.save

I have already done the below things
```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Impavidus on 2014-06-21
Your sumo, from the ppa, depends on libgdal1. This package is not available from the Trusty repositories and shouldn't be, as it is broken by libgdal1h (a different version of the same), which may be required by other applications. But is there anything wrong with the sumo package available from the repos? You may not need the ppa, which doesn't seem to be properly updated for Trusty.

You have quite a lot of ppas. They are known for breaking things, so use them sparingly.

---

