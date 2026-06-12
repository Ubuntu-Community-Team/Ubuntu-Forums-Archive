---
title: "[SOLVED] Broadcom wifi trouble"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by spencercarran on 2008-07-05
Hey,
New to Linux and having difficulty getting my wireless internet to work. I've got one of those accursed Broadcom 43xx wireless cards and can't figure out how to get my internet working on Ubuntu. I did manage to set up my dual-boot system in Ubuntu/MacOSX, but without internet the Ubuntu side is pretty limited. Any advice?

---

### Post by anewguy on 2008-07-05
There are many many threads on this in this forum and the archived forum.  Try a "search" with "Broadcom wireless" and see if any of those can help you.  If not, post back.  Just so you know, there are currently 2 ways of getting this to work:  ndiswrapper using the Windows driver or using the firmware cutter.  Both will get you to the same place - a working wireless card.  It's just a matter of personal choice - I myself just happen to like ndiswrapper.

I'm not trying to pass the buck here - it's just that there are so many threads on this subject.  After you do a search if you need help be sure to post back here!  :)

---

### Post by pHreaksYcle on 2008-07-05
Tell me which card and I will have a copy and paste guide in a matter of 5 minutes, maybe less. Then again, so should you :P

---

### Post by spencercarran on 2008-07-05
> **pHreaksYcle said:**
> Tell me which card and I will have a copy and paste guide in a matter of 5 minutes, maybe less. Then again, so should you :P

Broadcom 4328, I'm using a Santa Rosa MacBook. I know, I should be able to find this stuff, but I've found myself somewhat confused by the ubuntu documentation. Also, I don't have internet access while booted up in Linux, because I don't have any ethernet set up, just wifi, and right now that's only functioning when I'm in OSX.

---

### Post by Kevbert on 2008-07-05
The best guide is [[COLOR="Red"]here.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560")
It's a bit involved but works well.  If you have any problems, please ask.

---

### Post by spencercarran on 2008-07-05
> **Kevbert said:**
> The best guide is [[COLOR="Red"]here.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560")
It's a bit involved but works well.  If you have any problems, please ask.

sudo apt-get install ndiswrpper-utils-1.9 gives the following output:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9

I think part of the issue I've had with these guides is that I don't have access to Ethernet or any other wired internet connection... I only have wireless on my laptop.

---

### Post by anewguy on 2008-07-05
You can load ndiswrapper directly from the installation CD.  Load up the Cd and open it in the file browser.  Navigate to pool/main/n/ndiswrapper.  Click on each of the 2 tar's there - one for the utilities, one for ndiswrapper common.  This will "untar" them and install ndiswrapper.

After that, you will need a copy of the Windows driver for your card.  You should be able to find these and download them, then find the .inf and .sys files and copy them to your desktop.  You can do that with any PC and then just copy the files needed to a media you can load on your laptop.

Once you have done that, post back here and we'll go from there.  It just takes a few steps but I need to get going to a friends' house for a while.  I'll check back later tonight.

:)

---

### Post by spencercarran on 2008-07-05
All right, I managed to get it working, finally. Thanks for the help. Ubuntu is pretty damn awesome once it has an internet connection.

---

### Post by UbuntuNerd on 2008-07-05
The b43 drivers (bcm43xx in mainline kernels, b43 and b43legacy in wireless-2.6 and 2.6.24 and later) are drivers for the 802.11 B/G family of wireless chips Broadcom produces. I think that prior to 8.04 the driver was named bcm43xx, and now it is simply b43. If when doing a fresh install of Hardy, i.e. 8.04, your Broadcom BCM43xx based wireless didn’t work, here is a single command that will most likely turn it on:

sudo apt-get install b43-fwcutter

---

