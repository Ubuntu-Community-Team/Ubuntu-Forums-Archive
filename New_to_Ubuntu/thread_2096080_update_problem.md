---
title: "update problem"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by kenmac2 on 2012-12-18
Hi,
I have Ubunutu 12.04.
Recently when I attempt to download listed updates, I am asked to use the disk with 12.10 on it.
Of course I don't have this disk and eventually the update manager crashes.
As I'm running 12.04, why am I expected to have a 12.10 disk?

kenmac2

---

### Post by Bashing-om on 2012-12-19
kenmac2; Hi !

As of now I have no idea as to why the "12.10" disk is being ask for. Let's see if we can get to the bottom of things and see what is going on, Post the out put of terminal commands:
```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d

```[INDENT][INDENT]one step at a time, gets there <== BDQ

[/INDENT][/INDENT]

---

### Post by kenmac2 on 2012-12-20
bashing-om
the first line results in "no such file or directory"
the second line results in "is a directory"

What are we actually doing here?

kenmac2

---

### Post by kenmac2 on 2012-12-20
Oops - I had another go and got a response.
I'll put it in later. 

kenmac2

---

### Post by kenmac2 on 2012-12-20
OK, the first result was due to a typo.
The correct result was:

```
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

The second line was "Is a directory"

kenmac2

---

### Post by Bashing-om on 2012-12-20
roger, will catch up later.

GMT-6 here.

---

### Post by magic belle on 2012-12-20
> **Bashing-om said:**
> roger, will catch up later.
 
GMT-6 here.
 
GMT+8 here

---

### Post by Bashing-om on 2012-12-20
kenmac2;

/etc/apt/sources.list -file- : do not know what to think;
a) Did you copy the entire file ? as What is posted is the last third of the file.
I do not understand why deb-src ->for backports main and restricted would be in the file.
(the 1st posted line)

b) sources.list.d: My error, is a directory. Just need to know if there exist an entry in that directory:
```
ls -la /etc/apt/sources.list.d
```[INDENT][INDENT]getting there is half the fun <== BDQ

[/INDENT][/INDENT]

---

### Post by kenmac2 on 2012-12-20
The contents of the directory:
```
total 12
drwxr-xr-x 2 root root 4096 Jul 16 22:29 .
drwxr-xr-x 6 root root 4096 Dec  3 11:30 ..
-rw-r--r-- 1 root root  175 Jul 16 22:29 google-earth.list

```

Sorry, I stuffed up the copy of the first - here it is again:
```
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted
deb http://au.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://au.archive.ubuntu.com/ubuntu/ precise universe
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise mai
```

kenmac2

---

### Post by Bashing-om on 2012-12-20
kenmac2;

So far, so good. I got it ! Let's do this:
In gedit I suggest remove this line:(make a back up first)
"deb cdrom: [ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2]/quantal"
```
 cp /etc/apt/sources.list /etc/apt/sources.list-orig
gksudo gedit /etc/apt/sources.list
```
save the file and exit back to the terminal.
Then do the updates; terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
```


should be good to go <== BDQ

---

### Post by arpanaut on 2012-12-20
Near the top of the sources.list output this:
```
deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted
```I don't know how it got there???
But to eliminate the cd from being called by the update/upgrade mechanism you will need to edit the file to read:
```
 #deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted                                         
``````
gksu gedit /etc/apt/sources.list
```to open the file with root permissions make it look like the line w/ # in it, save then the update/upgrage should work correctly.

The real curiosity is how that entry got there in the first place?

---

### Post by kenmac2 on 2012-12-20
From the first line I get:
```
cp /etc/apt/sources.list /etc/apt/sources.list -orig
cp: invalid option -- 'o'
Try `cp --help' for more information.
```kenmac2

---

### Post by kenmac2 on 2012-12-20
Thank you* arpanuat*, that fixed it.

kenmac2

---

