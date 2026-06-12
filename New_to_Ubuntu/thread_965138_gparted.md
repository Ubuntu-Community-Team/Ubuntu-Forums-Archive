---
title: "gparted"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by johntravis on 2008-10-31
Once again I am lost. I have burnt a gparted-live and a .iso image, on seperate cd's.Put in order,in bios, start-up-- optical,floppy,hdd. put gparted in tray-started,(booted) ubuntu 8.0.4,according to instructions hit enter upon boot screen. This is where I am lost,ubuntu started normaly,no gparted,help is needed please.  Want to dual boot ubuntu 8.0.4 with 8.10

---

### Post by unutbu on 2008-10-31
It may be that there is a problem with how the GParted LiveCD was burnt. For example, the machine might have tried to boot from the CD, found that it couldn't, and then reverted to booting from the hard drive.

You said that you burnt 2 CDs... the GParted LiveCD and a .iso. I'm not sure why. When you want to make a bootable CD, Nautilus will recognize that you are burning an iso file and ask you if you want to make a bootable CD. If you don't get this message, it may be that your CD burning program tried to burn the iso file as a regular data file. This might explain the error, but then again, this is just a guess.

Also, it may not be necessary to use a GParted LiveCD. If you are installing Ubuntu 8.10, then you probably have an Ubuntu 8.10 LiveCD. This LiveCD has gparted on it already.

---

