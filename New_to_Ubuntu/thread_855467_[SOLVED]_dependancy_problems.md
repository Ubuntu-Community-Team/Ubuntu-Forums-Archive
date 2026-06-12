---
title: "[SOLVED] dependancy problems"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-10
i have heard that other people have 8.04 or 8.04.1,i have the latter,but while those others have no problem compiling blender or downloading alien arena,icant do any of those but the error messages dont tell me what the dependency is,and if the others have no problem then there must be a work around.can anyone suggest a fix,because theres alot i cant download,is this a bug or is my system to new for the repositories?????:confused:

---

### Post by deNoobius on 2008-07-10
> **rixtr66 said:**
> i have heard that other people have 8.04 or 8.04.1,i have the latter,but while those others have no problem compiling blender or downloading alien arena,icant do any of those but the error messages dont tell me what the dependency is,and if the others have no problem then there must be a work around.can anyone suggest a fix,because theres alot i cant download,is this a bug or is my system to new for the repositories?????:confused:

All you have to do with Blender is extract it--I just got it last night.  What error are you getting?

---

### Post by tjwoosta on 2008-07-10
when installing .deb's from synaptic (like alien arena) it should automatically ask you if you want to install the required dependencies (as all the dependencies for alien arena are infact availible in synaptic)

---

### Post by rixtr66 on 2008-07-10
ok i got blender ok but im still having trouble with alien arena right
now get deb isnt working but i still cant get through synaptic,or add remove
the error says somthing about getting ver 6????

---

### Post by mcduck on 2008-07-10
THere is no difference between 8.04 and 8.04.1 after installed and updated. 8.04.1 is just and updated version of the i8.04 install diskthat includes updates that have been released after the initial 8.04 release.

Actually it makes no difference if you install Ubuntu with 8.04 Alpha, 8.04 Beta, 8.04 RC, 8.04 or 8.04.1 disk. After installing all updates you get exactly same setup.

Anyway, could you post the _exact_ error message you get when trying to install from repositories?

---

### Post by rixtr66 on 2008-07-10
rick@rick-laptop:~$ sudo apt-get install alien-arena
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  alien-arena: Depends: alien-arena-data (>= 7.0) but 6.10-1 is to be installed
E: Broken packages
rick@rick-laptop:~$ 

rick

---

### Post by bapoumba on 2008-07-10
> **rixtr66 said:**
> rick@rick-laptop:~$ sudo apt-get install alien-arena
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  alien-arena: Depends: alien-arena-data (>= 7.0) but 6.10-1 is to be installed
E: Broken packages
rick@rick-laptop:~$ 

rick
Please post your sources.list:
```
cat /etc/apt/sources.list
```
You may not have the multiverse repos enabled or have repos for several ubuntu versions.

---

### Post by rixtr66 on 2008-07-10
ck@rick-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
rick@rick-laptop:~$ 
rick

---

### Post by bapoumba on 2008-07-10
Strange, the package from the backports requires [alien-arena-data  (>= 7.0) ]("http://packages.ubuntu.com/hardy-backports/alien-arena"), but [I cannot find it for hardy or in the backports]("http://packages.ubuntu.com/search?keywords=alien-arena-data&searchon=names&suite=all&section=all").
So remove the backports (and both cdroms while you are at it). You can do it from synaptic or by editing the sources.list:
```
sudo nano /etc/apt/sources.list
```

Place a # in from of the cdrom lines (for hardy and gutsy) and the backports, save the file with CTRL-O (same name, hit enter), exit nano with CTRL-X, reload the file:
```
sudo apt-get update
```
and try to install alien-arena again.

There may be a problem with the upload of the dependencies inthe backports.

---

### Post by rixtr66 on 2008-07-10
E: Malformed line 1 in source list /etc/apt/sources.list (URI)

---

### Post by rixtr66 on 2008-07-10
ok i typed wrong at first but then corrected it and your suggestion worked.
thanx,how long does it take to learn this stuff??????
rick

---

### Post by tjwoosta on 2008-07-10
ok i figured it all out


you need to install alien-arena-data first!


if you got the package from getdeb.net the alien-arena-data should be right beside it

or its also in synaptic

sorry i missed this before (could have saved you alot of time)


EDIT: just read the previous post  (glad you got it sorted)

---

### Post by bapoumba on 2008-07-11
> **rixtr66 said:**
> ok i typed wrong at first but then corrected it and your suggestion worked.
thanx,how long does it take to learn this stuff??????
rick
Depends. I like much packages managers, and I've learned a lot by helping others, and reading the basics on Debian tutorial pages.

---

