---
title: "Hardware Drivers for Dell Inspiron 1525 on Xubuntu 14.04.2 LTS (trusty)"
date: 2015-04-28
forum: New to Ubuntu
---

### Post by Mark_McDonald on 2015-04-28
I am obviously a newbie. I just realized something from another post I read.
I need drivers. As the title says I have a Dell Inspiron 1525 laptop.
From Terminal I used "sudo lshw -short" 
I get this..... Its 32bit, Intel Pentium 1.6Ghz dual core, 1GB of DDR (667Mhz), 120GB HD (110GB+1GB partition)

I have a wireless mouse via usb tx/rx (I believe). 

Problem I am having and it was more previlent in Ubuntu, is my mouse would stop working all together. I would try moving the mouse around on different surfaces. When I have qBittorrent going that would freeze too, so that told me the system crashed.
I would let sit for some time, come back to it and it would still be frozen. Another note is I am also using a 2TB external Hard Drive via usb port and my system is most likey USB 1.0 or if I am lucky a USB 2.0. So my transfer speeds are slowed but its managable.
Most of the time (90%) it will crash when I am not transferring files over to 2TB ext. HD. 

So am I suppose to download drivers for my BIOS, onboard video, mouse, ext. hd, dvd +/- RW, IDE/SATA etc Controllers. Could this be whats causing my system to crash every now and then.

The behaviour is I will have qBittorrent downloading, Firefox open, I rarely use Terminal window, might have pyRenamer, or a VPN program going. Most of the time though I will have my ext hd file open, along side my internal HD shared folder open as well. Thats when I transfer files from shared int hd to unshard ex hd. Yeah sometimes I will have Software Center open, but not downloading nothing.

Any help would be appreciated for this n00b!

---

### Post by RobGoss on 2015-04-28
this is SiriThis Dell website should allow you to download the necessary drivers in order to update your bios, [http://www.dell.com/support/home/us/en/19/Products/?app=drivers](http://www.dell.com/support/home/us/en/19/Products/?app=drivers) , as far a your machine crashing this can be cased by a number of things. If I were you I would consider adding some more ram it always increases the performance of your machine.

---

### Post by Geoffrey_Arndt on 2015-04-28
Mark . . . I suspect the basic issue is your PC is just too wimpy for Ubuntu.   Barely enough ram (2 Gb recommended for most machines).  Relatively older, slow processor, etc.   Drivers (or lack of) is likely NOT the issue.

Anyway, the good news is the fix is simple.    Run a lighter distro (such as Xubuntu) or even better, a great distro for real newbies is Linux Mint . . . on your machine Mint with the Mate desktop (latest version is 17.1 if I recall right).   Mate should be much more responsive on your machine.

---

### Post by cariboo on 2015-04-28
If you are going to install Mint, and then add the mate desktop, why not just install Ubuntu Mate 15.04, seeing as it is now an official derivative.

---

### Post by Geoffrey_Arndt on 2015-04-29
Either Mint or Ubuntu Mate are a good lighter choice for an older PC, but an LTS version may be better for a newbie.   No need for upgrade or reinstall till 2019 unless he wants to.

---

### Post by Norm24 on 2015-04-29
> **Geoffrey_Arndt said:**
> Mark . . . I suspect the basic issue is your PC is just too wimpy for Ubuntu.   Barely enough ram (2 Gb recommended for most machines).  Relatively older, slow processor, etc.   Drivers (or lack of) is likely NOT the issue.

Anyway, the good news is the fix is simple.    Run a lighter distro (such as Xubuntu) or even better, a great distro for real newbies is Linux Mint . . . on your machine Mint with the Mate desktop (latest version is 17.1 if I recall right).   Mate should be much more responsive on your machine.

I have the same exact laptop running Ubuntu14.04....runs like a champ in Unity,Gnome-shell and Gnome-fallback.Drivers for me were never an issue,everything worked great right from the beginning.The Xfce desktop is pretty lightweight...but I would agree it certainly "sounds" like a ram issue its just hard to believe Xubuntu won't run on 2GBs as 512MBs is the min required.

Mark you may also want to consider Lubuntu?Or simply try upgrading your mem.....simms are pretty cheap for older machines.Can't hurt to update drivers.

---

