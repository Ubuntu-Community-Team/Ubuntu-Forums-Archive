---
title: "Sources Problem -- can't run anything"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by StevenHodges92 on 2013-12-31
I can't seem to run anything it seems, for example the synaptic package manager and my software center freezes upon startup

in terminal gedit /etc/apt/sources.list shows this:

> # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
# deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) dapper main # disabled on upgrade to raring

---

### Post by StevenHodges92 on 2013-12-31
Now I refreshed my sources to this

> 
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted universe multiverse 



and sudo apt-get update gives me this

 Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

---

### Post by steeldriver on 2013-12-31
sounds like the same issues as this --> [http://ubuntuforums.org/showthread.php?t=2195763](http://ubuntuforums.org/showthread.php?t=2195763)

---

### Post by grahammechanical on 2013-12-31
To put in another way. Medibuntu no longer exists. The maintainer has ceased maintaining it. So, you need to remove medibuntu from your sources list and then the error message will go away.

I would not advise upgrarding Ubuntu to a newer version without first taking Ubuntu back to a default situation. Remove PPAs. Set a default theme. Do stuff like that because the upgrade scripts are only designed to upgrade Ubuntu and not the personally modified versions of Ubuntu that we are running. Less problems this way.

Regards.

---

### Post by StevenHodges92 on 2013-12-31
So what do I edit in my short sources list to remove Medibuntu?  Sorry I'm really new with Ubuntu.

---

### Post by ajgreeny on 2013-12-31
In synaptic go to **Settings ->Repositories ->Other Software** tab and remove or disable medibuntu there.

---

### Post by StevenHodges92 on 2013-12-31
When I open Synaptic I get this

> E: Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

and then synaptic closes, can I do it through the terminal and if so how do I do it?

---

### Post by oldos2er on 2013-12-31
```
sudo rm /etc/apt/sources.list.d/medibuntu*

sudo apt-get update
```

Just FYI, you should use code tags instead of quote tags when posting terminal output.

---

