---
title: "Removing XUbuntu"
date: 2015-06-19
forum: New to Ubuntu
---

### Post by michael290 on 2015-06-19
```
michael@michael-Aspire-5335:~$ sudo apt-get remove xubuntu-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xubuntu-plymouth-theme' for regex 'xubuntu-*'
Note, selecting 'plymouth-theme-xubuntu-logo' for regex 'xubuntu-*'
Note, selecting 'xubuntu-core' for regex 'xubuntu-*'
Note, selecting 'xubuntu-desktop' for regex 'xubuntu-*'
Note, selecting 'xubuntu-restricted-extras' for regex 'xubuntu-*'
Note, selecting 'xubuntu-artwork' for regex 'xubuntu-*'
Note, selecting 'plymouth-theme-xubuntu-text' for regex 'xubuntu-*'
Note, selecting 'xubuntu-community-wallpapers' for regex 'xubuntu-*'
Note, selecting 'xubuntu-default-settings' for regex 'xubuntu-*'
Note, selecting 'ubiquity-slideshow-xubuntu' for regex 'xubuntu-*'
Note, selecting 'xubuntu-docs' for regex 'xubuntu-*'
Note, selecting 'xubuntu-live-settings' for regex 'xubuntu-*'
Note, selecting 'ldm-xubuntu-theme' for regex 'xubuntu-*'
Note, selecting 'xubuntu-restricted-addons' for regex 'xubuntu-*'
Note, selecting 'xubuntu-icon-theme' for regex 'xubuntu-*'
Note, selecting 'xubuntu-wallpapers' for regex 'xubuntu-*'
Package 'xubuntu-plymouth-theme' is not installed, so not removed
Package 'ldm-xubuntu-theme' is not installed, so not removed
Package 'ubiquity-slideshow-xubuntu' is not installed, so not removed
Package 'xubuntu-core' is not installed, so not removed
Package 'xubuntu-live-settings' is not installed, so not removed
Package 'xubuntu-restricted-addons' is not installed, so not removed
Package 'xubuntu-restricted-extras' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libltdl7 : Breaks: libltdl7:i386 (!= 2.4.2-1.10ubuNtu1) but 2.4.2-1.10ubuntu1 is to be installed
 libltdl7:i386 : Breaks: libltdl7 (!= 2.4.2-1.10ubuntu1) but 2.4.2-1.10ubuNtu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
michael@michael-Aspire-5335:~$ apt-get remove xubuntu-desktop
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
michael@michael-Aspire-5335:~$ root
The program 'root' is currently not installed. You can install it by typing:
sudo apt-get install root-system-bin
michael@michael-Aspire-5335:~$ sudo apt-get install root-system-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libltdl7 : Breaks: libltdl7:i386 (!= 2.4.2-1.10ubuNtu1) but 2.4.2-1.10ubuntu1 is to be installed
 libltdl7:i386 : Breaks: libltdl7 (!= 2.4.2-1.10ubuntu1) but 2.4.2-1.10ubuNtu1 is to be installed
 root-system-bin : Depends: libroot-core5.34 (>= 5.34.19+dfsg) but it is not going to be installed
                   Depends: libroot-io5.34 (>= 5.34.19+dfsg) but it is not going to be installed
                   Depends: root-plugin-graf2d-asimage but it is not going to be installed
                   Recommends: root-plugin-graf3d-gl
                   Recommends: libroot-math-minuit or
                               root-fitter
                   Recommends: libroot-core-dev but it is not going to be installed
                   Recommends: root-plugin-graf2d-x11 but it is not going to be installed or
                               root-system-display
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

---

### Post by Bucky Ball on 2015-06-19
And? If you want to completely remove Xubuntu, boot from live media, launch Gparted, delete the partition. Done. 

You give no specifics here about what your end-goal is, or about much else. The way you've gone about this, though, is not the way one normally would. What do you expect to end up with after this command? What do you expect the machine to do when you next boot after this command and what state do you expect the hard drive to be in, re. partitioning? That command will leave you with one screwed up, probably unbootable, partition.

---

### Post by dino99 on 2015-06-19
so , what are you trying to do by removing a bunch of xubuntu packages ?

---

### Post by Bucky Ball on 2015-06-19
> **dino99 said:**
> so , what are you trying to do by removing a bunch of xubuntu packages ?

*Exactly* what I just asked.

---

### Post by RobGoss on 2015-06-19
Kind of confusing what he's trying to accomplish here.

---

### Post by v3.xx on 2015-06-19
Ok, this is a job for my crystal ball.
```
sudo apt-get remove xubuntu-*
```
A valiant effort, but as you found out, won't work.

You can now spend hours (if not days) trying to repair this.  Or ..
Time to reinstall.

---

### Post by michael290 on 2015-06-19
i am seeing if this might help my other problem

i am trying to upgrade to 15.04

---

### Post by Bucky Ball on 2015-06-19
Upgrading a broken install via the net has a 99% chance of fixing nothing. If you are going to try 15.04, do a clean install. If you have issues with a clean install of 15.04, please post a new thread about it with a descriptive title.

As you have given us no information whatsoever about what you are trying to do, apart from remove Xubuntu, despite requests for the information and have not responded to questions it is hard to help you in anyway. Apart from a slab of code which gives an indication of the mess your machine is in we've nothing to go on, but from that output, and from the way you've attempted to uninstall Xubuntu, you have been given the advice to reinstall, which you've also ignored. 

I also gave you clear instructions for wiping the drive with Gparted on the first line of the second post in this thread.

Please give us some detail if you want support. Without it, and some responses to those attempting to help, this thread serves little purpose. Thanks.

---

