---
title: "Install help: GUI doesn't load"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by eoren1 on 2008-06-08
Absolute newbie here looking for help with an install:
I'm trying to install Kubuntu 7.10 in order to use LinuxMCE.  This is going on what is now my Vista PC with a GA-73UM-S2H (NVIDIA GeForce 7150 / nForce 630i Chipset) motherboard.  I started off by shrinking my C drive to open up about 16 gigs of unformatted space.  Downloaded the Kubuntu 7.10 32 bit iso and burned the CD.  When I boot from the CD, I get the first screen offering the choice of installing Kubuntu.  However, after a few minutes and what looks like a number of 'ok' messages, I end up in a terminal type screen.  I never get the GUI that is supposed to bring me to the Install Wizard.
Would greatly appreciate any and all advice.
E

---

### Post by superprash2003 on 2008-06-08
is it the busybox screen?

---

### Post by eoren1 on 2008-06-08
> **superprash2003 said:**
> is it the busybox screen?

I don't think so.  Just a black screen with text prompt.  Lists common functions for install (sodu?).  Looks just like my terminal prompt on my Macbook.

---

### Post by PmDematagoda on 2008-06-08
If it isn't BusyBox, then try starting the X-Server with:-
```
startx
```

---

### Post by eoren1 on 2008-06-08
Thanks for indulging a newbie.
I retried the install CD this time with 'safe graphics mode' and it worked!
E

---

### Post by eoren1 on 2008-06-08
So kubuntu is now installed!
Quick question on the appropriate NVIDIA drivers.  They say they support the following:

Supported Distributions:

    * RHEL5U1
    * RHEL5
    * RHEL4U6
    * RHEL4U5
    * RHEL4U4
    * RHEL3U9
    * RHEL3U8
    * RHEL3U7
    * SuSE10.2
    * SLES10.1
    * SLES10
    * Fedora Core 7
    * Fedora Core 6

Which do I use for Kubuntu 7.10?
Thanks
E

---

### Post by PmDematagoda on 2008-06-08
What's the VGA card you use?

---

### Post by eoren1 on 2008-06-08
It's integrated into the motherboard: NVIDIA GeForce 7150 / nForce 630i Chipset

---

### Post by PmDematagoda on 2008-06-08
Install the Nvidia-glx-new package with:-
```
sudo apt-get install nvidia-glx-new
```
and enable it with:-
```
sudo nvidia-xconfig
```
then see if your Nvidia card works properly.

---

