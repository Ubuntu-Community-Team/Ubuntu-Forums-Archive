---
title: "synaptic problem"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by HunkieChan on 2008-10-13
when i try to open synaptic. i get this error. how can i fix this ?

An error occured

The following details are provided:

E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by meanburrito920 on 2008-10-13
weird. I would suggest uninstalling and reinstalling synaptic. Only synaptic. so:

$ sudo apt-get remove synaptic
$ sudo apt-get install synaptic

---

### Post by mc4100 on 2008-10-13
Backup the file (/var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages) first, then try:
```
sudo rm /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages; sudo apt-get update
```

---

### Post by HunkieChan on 2008-10-13
bro whats the command line to back up ?

---

### Post by RequinB4 on 2008-10-13
> **HunkieChan said:**
> bro whats the command line to back up ?

```

sudo cp /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages.backup
```

Why is it spelled harty and not hardy? ...

---

### Post by HunkieChan on 2008-10-13
uh, im still getting that error

Fetched 479kB in 1min10s (6821B/s)                                             
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by Liviu-Theodor on 2008-10-13
Have you checked first the Internet connection? Seems that is in fact the problem, internet connection lost.

---

### Post by HellNoire on 2008-10-13
I've got internet connection and have the same issue. I have done all that is said here and am waiting on more answers to try. Might it be an issue with one of the old updates? I know I recently installed Medibuntu, Skype, aMSN, and The Gimp 2.6.1

---

### Post by Liviu-Theodor on 2008-10-13
Have you also tried to remove any extra repository from the Software Sources? What happens if you use only the standard repositories?

---

### Post by Kevbert on 2008-10-13
Please post your /etc/apt/sources.list file.

---

### Post by MightyMag on 2008-10-13
I have got the exact same problem. Just happend a while ago.

Edit:
I solved it.
> sudo gedit /etc/apt/sources.list
Then I put a # on every line that had "harty" in it. For it was:
deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all
deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all
They were all under "#ULTAMATIX REPOS START" so it could be a problem with Ultamatix.
After that I did > sudo aptitude update

---

### Post by AlanStretton on 2008-10-13
I had the same problem.

I removed the following 2 lines from my etc/apt/sources.list file by using the #  at the start of each line


#deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

#deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

I cannot remember how these lines got there in the first place.

Alan

---

### Post by Kevbert on 2008-10-13
If your using Ubuntu Ultimate the lines should read:
```
deb http://repoubuntusoftware.info[COLOR="Red"]/[/COLOR] harty all
deb http://repoubuntusoftware.info[COLOR="Red"]/[/COLOR] harty all 
```

---

### Post by Disident on 2008-10-13
> **Kevbert said:**
> If your using Ubuntu Ultimate the lines should read:
```
deb http://repoubuntusoftware.info[COLOR="Red"]/[/COLOR] harty all
deb http://repoubuntusoftware.info[COLOR="Red"]/[/COLOR] harty all 
```

Doesn't worked for me, needed to put # before them.

---

### Post by Kevbert on 2008-10-13
If you put # at the beginning of a line it's treated like a comment (i.e. ignore, no action).  I've posted on the Ultimate forum to see if there's a problem there and cross referenced it to another post on this forum with the same problem.

---

### Post by Kevbert on 2008-10-13
Replace harty with hardy - You'll now get a http 404 error (page not found).
Will update when fixed.

---

### Post by Kevbert on 2008-10-13
Apparently the problem is due to some servers being upgraded which may take a little while.  Until then the choice is either to comment out the offending sources.list line with a # or to ignore the 404 error.  Updates on the problem will be provided on the Ultimate forum under News.

---

### Post by brcre on 2008-10-13
Open a terminal and copy and paste the following line. Hit Enter

```
sudo perl -pi -e s^harty^hardy^g /etc/apt/sources.list;sudo apt-get update; sudo apt-get upgrade
```

The bug appears to be fixed now...at least on the one computer I've received this error on and repaired it.

---

### Post by javiersd on 2008-10-14
worked for me with post # 12 
thanks every one 
im new in ubuntu and this is the best tech support ever

---

### Post by HunkieChan on 2008-10-14
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

## Medibuntu - Ubuntu 8.04 "hardy" 
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/) 
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free


#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main
deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main

---

### Post by HunkieChan on 2008-10-14
> **Kevbert said:**
> Please post your /etc/apt/sources.list file.

> **brcre said:**
> Open a terminal and copy and paste the following line. Hit Enter

```
sudo perl -pi -e s^harty^hardy^g /etc/apt/sources.list;sudo apt-get update; sudo apt-get upgrade
```

The bug appears to be fixed now...at least on the one computer I've received this error on and repaired it.

thanks bro. it worked.

---

