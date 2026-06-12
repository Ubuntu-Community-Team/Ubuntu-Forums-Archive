---
title: "always failed to install packages with all dependencies satisfied!!"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by paranoid_humanoid on 2008-04-30
hi, i've recently noticed that no deb package that i try to install get installed. even some deb packages that i have installed before and am sure of its integrity.
all goes well, all dependencies are satisfied, it asks for the root password, then in the terminal window it says "(Reading database..." then it stops and says "failed to install package..."..
i think it started a couple of days ago since i upgraded to hardy.. it's really frustrating. what should i do? :(

---

### Post by oldos2er on 2008-04-30
Check Software Sources to be sure all repositories are enabled.

---

### Post by paranoid_humanoid on 2008-04-30
> **oldos2er said:**
> Check Software Sources to be sure all repositories are enabled.
i'm trying to install a deb package that i got from getdeb.com, not from a repository.. does that make a difference!?

---

### Post by paranoid_humanoid on 2008-04-30
so no one has a clue why this is happening to me?! :(

---

### Post by oldos2er on 2008-04-30
Did you check Software Sources? If the *deb file needs to pull dependencies from the repositories, but can't find any, it's going to complain.

---

### Post by paranoid_humanoid on 2008-05-01
it didn't say that it needed other packages, it wasn't trying to download other dependencies..
and here are my sources: (attached screenshot)

---

### Post by seshomaru samma on 2008-05-01
please post your sources from the sources list
you can find that by running the command:
```
cat /etc/apt/sources.list
```
also try 
```
sudo apt-get update
```
and then
```
 sudo apt-get install -f
```

---

### Post by paranoid_humanoid on 2008-05-01
here's my sources.list

> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hardy main universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main


i forced to check for system-wide broken dependencies and it came back negative. none broken..
i tried installing a deb using dpkg from the terminal and it totally worked!!!
isn't the gui using dpkg as well? why is it failing then!!!

---

### Post by paranoid_humanoid on 2008-05-02
my problem still presists :(

if i want to install any deb pack, i have to dpkg it from the terminal window...

:'(

---

### Post by seshomaru samma on 2008-05-03
I would imagine there is some problem with apt
can you post the output of:
```
sudo apt-get update
```
```
sudo apt-get -f install
```
```
sudo apt-get --fix-missing
```
```
sudo apt-get --fix-broken
```

---

