---
title: "[SOLVED] Error in synaptic Package Manager"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by dc_jt on 2008-07-17
Hi I installed UBuntu 8.04 yesterday and today Ive been getting the following error when trying to apply all upgrades in the synaptic package manager:

E: /var/cache/apt/archives/sysvinit-utils_2.86.ds1-38_i386.deb: trying to overwrite `/usr/share/man/man1/mesg.1.gz', which is also in package sysvutils

Also I got a notification saying:

Sorry, the package "sysvinit-utils 2.86.ds1-38" failed to install or upgrade.

Hopefully it is all linked, any ideas??

Im a bit of a noob so if you could try and help that would be great.

Thanks

---

### Post by dc_jt on 2008-07-17
Anyone?!

I dont seem to be able to shutdown the computer now either. When I click shutdown, it doesnt restart the whole computer but it restarts Ubuntu so I have to log in again?

---

### Post by JoshuaRL on 2008-07-17
Go to Applications->Accessories->Terminal and input the following one at a time:
```

sudo apt-get clean -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall sysvinit-utils 2.86.ds1-38

```
and see if that helps.

What I'm trying to get you to do here is to first do a little housecleaning, then try to reinstall that package.  The first two commands clean out and fix APT and dpkg, and then the second two try to update your system.  Then the last is the reinstall.  If that doesn't work we can see if Synaptic can fix it.

---

### Post by dc_jt on 2008-07-17
> **JoshuaRL said:**
> Go to Applications->Accessories->Terminal and input the following one at a time:
```

sudo apt-get clean -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall sysvinit-utils 2.86.ds1-38

```
and see if that helps.

What I'm trying to get you to do here is to first do a little housecleaning, then try to reinstall that package.  The first two commands clean out and fix APT and dpkg, and then the second two try to update your system.  Then the last is the reinstall.  If that doesn't work we can see if Synaptic can fix it.

THanks for the reply. When I try and re-install it I get this message:

david@david-desktop:~$ sudo apt-get install --reinstall sysvinit-utils 2.86.ds1-38
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.86.ds1-38

??

---

### Post by JoshuaRL on 2008-07-17
> **dc_jt said:**
> THanks for the reply. When I try and re-install it I get this message:

david@david-desktop:~$ sudo apt-get install --reinstall sysvinit-utils 2.86.ds1-38
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.86.ds1-38

??

Sorry, try this:
```

sudo apt-get install --reinstall sysvinit-utils_2.86.dsl-38

```

---

### Post by dc_jt on 2008-07-17
> **JoshuaRL said:**
> Sorry, try this:
```

sudo apt-get install --reinstall sysvinit-utils_2.86.dsl-38

```

Thanks again for the reply but still the same unfortunately.

Any idea why?

---

### Post by dc_jt on 2008-07-17
Anyone help please?

Could it be something to do with the repositories?

---

### Post by plucky on 2008-07-17
I cannot find that package in my synaptic package manager.The closest is "sysvinit" package.
Can you post your sources.list file ```
cat /etc/apt/sources.list
``` and post the output.I am wondering if you have the "Proposed" and "Backport" repositories installed in you sources.list file.

Thanks.

---

### Post by dc_jt on 2008-07-17
Thanks for the reply, please see below:

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://ftp.debian.org](http://ftp.debian.org) etch main
```

---

### Post by plucky on 2008-07-17
> deb [http://ftp.debian.org](http://ftp.debian.org) etch main

That is the only difference I can see between your sources.list and mine.It might be worth commenting out that repository by accessing **System > Administration > Software Sources** and un-ticking that repository in the "Third Party Software" tag and then reloading.

Good Luck

p.s. Is there a reason for having the DEBIAN.ORG repository?

---

### Post by dc_jt on 2008-07-17
THat seems to have got rid of the update, maybe I didnt need it?! 

Oh well. Hopefully everything should be ok now. 

I still cant shutdown my computer though, is this a known bug?

---

### Post by c0met on 2008-07-17
Does the "Quit" under "System" also logout rather than shutdown?

---

### Post by plucky on 2008-07-17
> I still cant shutdown my computer though, is this a known bug? 

Some people have had problems with shutting down,but I don't know of a fix for it.Perhaps you should start another Thread with an appropriate title so that someone can help you.

Please mark this thread as solved, if it is solved, using the Thread tools at the top of the Page.

Thanks.

---

### Post by JoshuaRL on 2008-07-17
> **dc_jt said:**
> THat seems to have got rid of the update, maybe I didnt need it?! 

Oh well. Hopefully everything should be ok now. 

I still cant shutdown my computer though, is this a known bug?

This is a great example as to why you don't want to mix distribution repositories.  Ubuntu should stay with it's own repos, and so should Debian.  You have problems like this, and could have hurt your system more.  So far the only problem seems to be fixed, so congratulations.

I did this once (added Ubuntu repos to Linux Mint that weren't there before) and it messed stuff up hardcore.  So unless you know exactly what you're doing and how to do it (APT pinning or package merging) I wouldn't suggest it.

---

