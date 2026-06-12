---
title: "Updates to ubuntu 12.04"
date: 2013-10-16
forum: New to Ubuntu
---

### Post by waltwin on 2013-10-16
I am advised that I have updates to ubuntu 12.04, but, when I select updates, I am required to install a CD containing 13.10. Why would I need to have a 13.10 CD  to install 12.04 updates?
   
  This only happens on my desktop machine. The problem does not exist on my laptop.
   
  Any clarification would be much appreciated.

waltwin

---

### Post by heir4c on 2013-10-16
See the Softwaresources (Software&Updates)(first Tab) And uncheck the cd (at the bottom of the screen)

---

### Post by deadflowr on 2013-10-16
You don't happened to have a copy of 13.10 in your cd drive right now, do you?
That can cause the issue.

But the otherwise stated advice is what you should do anyway.

Easiest way is to open update manager and select settings in the bottom left, which will open the software sources.
proceed as stated above.

odd if there's a listing for 13.10 though.

---

### Post by waltwin on 2013-10-16
> **heir4c said:**
> See the Softwaresources (Software&Updates)(first Tab) And uncheck the cd (at the bottom of the screen)

I don't see anything about "Software&Updates" and no CD at the bottom of the screen! Am I looking in the wrong place?

---

### Post by deadflowr on 2013-10-16
> **waltwin said:**
> I don't see anything about "Software&Updates" and no CD at the bottom of the screen! Am I looking in the wrong place?

That's because "software and updates" doesn't exist on 12.04.

Follow my above advice on using update manager to get to the software sources.
Which is what, in essence, software and updates is, or will be in versions past 12.04.

The nice thing about using update manager, is that when you close the software sources window, you can run "check" and it will proceed to refresh the package list.

---

### Post by fantab on 2013-10-17
Or you can use the 'Software Center' -> Edit -> Software Sources
You probably have CD selected, just unselect it.

---

### Post by waltwin on 2013-10-22
I have done everything that has been recommended. In the majority of the cases the items that I am supposed to change do not exist, such as un-checking CDs and the like.
   
  I downloaded Saucy Salamander but no joy there. I am no software weenie and I envy those of you who are. I just like ubuntu and it makes me crazy when it appears that I will no longer be able to update my current system.
   
  Thanks to everyone who tried to help as it is greatly appreciated.
   
  waltwin

---

### Post by deadflowr on 2013-10-22
Okay then, let's try the ole manual method, if yuou don't mind.

Open up a terminal and run
```
gksu gedit /etc/apt/sources.list
```
You should have a file that looks like this
```
deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


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
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main



```

Add a comment ( the # symbol means a comment; comments = ignore, from the systems point of view, as the system will ignore any line with that in front) to the lines containing deb cdrom( they are usually at the beginning of the file).
Then save and close, then run
```
sudo apt-get update
```

---

### Post by fantab on 2013-10-23
If you are on Saucy Salamander then instead of 'gksu' use 'sudo'.
```
gksu gedit /etc/apt/sources.list
sudo gedit /etc/apt/sources.list
```
If you don't benefit from the 'deadflowr's' above post then from the terminal run the following commad, copy all of its output in the terminal and paste the output here.

```
cat /etc/apt/sources.list
```

---

### Post by waltwin on 2013-10-25
That fixed it. I have down loaded 128 individual updates. I really appreciate the information. I have one Windows machine that I use when ubuntu won’t copy a document accurately, sometimes additional characters are added. Even with their spyware protection it is corrupted. I have been using ubuntu for several years and I can’t imagine ever returning to Windows.
   
  waltwin

---

### Post by fantab on 2013-10-25
Glad you've got it. Now Mark the Thread as 'Solved' using Thread Tools.

---

