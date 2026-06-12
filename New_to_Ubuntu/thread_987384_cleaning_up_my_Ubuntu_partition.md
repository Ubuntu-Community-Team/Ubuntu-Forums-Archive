---
title: "cleaning up my Ubuntu partition"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Algus on 2008-11-19
I've got a Sony laptop with a 60GB HDD partitioned for an Ubuntu installation and a WindowsXP installation.  

I set this up back in the Ubuntu 7.10 days and eventually updated it to 8.04.  I dusted the machine off today as I'm going to need to use it for awhile (my desktop is down) and I think I need to do some housekeeping on the OS but I'm not sure of the steps I need to take.  

When I use the updater I end up getting an error with Ubuntu claiming it couldn't download all of the packages (it got about half of them).  It also said that I needed to do a "partial install" before I could start getting the updates.   At any rate, the updater program doesn't work at all.  

Since it's an older laptop I'd like to get XFCE on it.  I used 

sudo aptitude update && sudo aptitude install xubuntu-desktop

To get the xubuntu desktop.  

I got the same error of only being able to do a partial upgrade (is this coming because I have 8.04?) though it didn't seem to have any problems during the update.

According to GRUB I've got two Linux kernals and my XP stuff (not a problem I guess? Im just trying to think of everything that my be pertinent) 

Here's the caveat to any repair job I do though - my CD drive is dying (works sometimes) so I guess I need to make a LiveUSB? (I have not done this, I have a thumb drive but I can't remember if it's 512MB or 1 GB)  

What I want to do is this
- Have Xubuntu 8.10 installed (regular Ubuntu is fine too I guess, Im working with a P4 and 768MB of RAM) 
- clean out anything unnecessary from my Linux partition

My startup is kind of slow (XFCE loads up fast, but Im wondering if there's anything I can tweak to get to the log on screen faster)  

Any help you guys could offer on how to fix things up would be great.

---

### Post by oldos2er on 2008-11-19
Can you post the output of "cat /etc/apt/sources.list"?

---

### Post by Algus on 2008-11-19
Slight update:

After I logged into an XFCE session I was able to get my machine fully updated.  However, now after rebooting my computer I cannot log back in to XFCE (the splash changes to the Xubuntu light blue background but the GUI never appears)  I might have broken something when I was fiddling with the log-in screen options (wanted to set it to the Xubuntu splash screen but as far as I know that's all I touched >.>) 

Here is the output you requested oldos2er.  Coincidently, after successfully updating in Xubuntu (which is now broken?) it seems there are no longer any updates for me. 

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
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

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


---

