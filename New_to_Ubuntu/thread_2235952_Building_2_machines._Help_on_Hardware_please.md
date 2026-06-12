---
title: "Building 2 machines. Help on Hardware please"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by Mrdx on 2014-07-23
Forgive me if I am in the wrong section for this.

I am in need of some advice please.
I need to build 2 machines that will be able to run Ubuntu and windows using whine.
I am asking for hardware advice that is supported by Ubuntu and win7 and or 8.
Both will be used for multimedia, spread sheets, and general daily work. They both need DVD/CD RW's and SD Card readers.  1 of them will also be used for video editing, real-time video and light gaming for the grand-kids.
Neither of them need hi-end graphics.
I would like to use 2 USB 3 ports in the front of the case.

So you have an idea. The main system I am using is a Del DXP051, Intel Pentium D CPU 3.00GHz, 2 Core. 4 gb ram, NVIDIA GeForce 7300 LE.  
As of the last 5 recent updates to win7, it has slowed down and the DVD/CD drives no longer work and some other issues.

If you all could help me with ideas on the hardware or advice for the systems I would appreciate it.

Thank you.

---

### Post by MartyBuntu on 2014-07-23
Budget?

---

### Post by Mrdx on 2014-07-24
Oh, that would help...  lol
$800 to $1k each

---

### Post by farrinux on 2014-07-24
> Both will be used for multimedia, spread sheets, and general daily work. They both need DVD/CD RW's and SD Card readers. 1 of them will also be used for video editing, real-time video and light gaming for the grand-kids.
Neither of them need hi-end graphics.
I would like to use 2 USB 3 ports in the front of the case.

As far as hardware goes. I can only advise you on an AMD platform.  I have several machines that would work.  The most recent one has the following hardware.

1. AMD Athlon X4 750K Trinity Quad-Core 3.4GHz Socket FM2 100W Desktop Processor - Black Edition AD750KWOHJBOX.   [http://www.newegg.com/Product/Product.aspx?Item=N82E16819113328](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113328)
2. GIGABYTE GA-F2A88X-UP4 FM2+ / FM2 AMD A88X (Bolton D4) HDMI SATA 6Gb/s USB 3.0 ATX AMD Motherboard.   [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128655](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128655)
3. G.SKILL Ripjaws Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Desktop Memory Model F3-10666CL9D-8GBRL.   [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231311](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231311)
4. GIGABYTE GV-N630-2GI REV3.0 GeForce GT 630 2GB 128-Bit DDR3 PCI Express 2.0 x16 Video Card.   [http://www.newegg.com/Product/Product.aspx?Item=N82E16814125483](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125483)

For hard drives there are four WD Blues. Two Asus DVD/CD- rw's. A combination card and floppy disk reader (It's old but still works. The floppy is not used).  I have used Rosewill card readers also. 

Other hardware that I use successfully with Win XP & 7.0 are from MSI (Motherboards & Nvidia based video cards), Geil (Memory), IOGEAR (Bluetooth) Rosewill (Card readers, USB hubs. PS, etc.) Logitech (Keyboards and mice & Joysticks.) Thrustmaster (Game controllers and Joysticks.), Anker Uspeed (PCI-E to USB 3 card.) 

Hope it helps. :p

---

### Post by Rob Sayer on 2014-07-24
Run "Windows using whine" (you mean Wine I suppose)?  That would actually involve running Windows *applications* using Wine.  Which is actually overrated.  It doesn't actually work that reliably, a fact that is extremely well documented.  This is a common noob mistake which generally leads to disappointment.

A far better solution would be to dual boot linux and windows.  The best, most reliable way to do that is to use 2 separate HDs but it can certainly be done on one.

Depending on what you mean by "video editing" you may need a lot more video card power than you assume.  The better NLE editors actually are power hungry.  Even a basic one like avidemux isn't that small.  You'll want a good chunk of RAM.  Just *playing* video isn't so bad though.

I prefer Intel machines over AMD because their linux support is far better (unless they outsource the graphics card as in my netbook).  A lot of ubuntu 12.04 users running AMD video cards that weren't new but not *that* old found one day that their screen was black when rebooting because AMD had dropped support for the new kernel.  It was fixable, but then the video performance sucked.  I have personal experience of this.

This wouldn't be a problem with a build using a non AMD video card but I'll still NEVER buy another AMD based computer.

---

### Post by Mrdx on 2014-07-24
farrinux.
Thank you for the advice. 
Ill look over all that in more detail. Looks good though.

---

### Post by Mrdx on 2014-07-24
Rob Slayer.
Thank you.
Yes, I do mean wine. I was playing with the word since some of my old crony buddies whine about it...
I do like the 2nd HD to install it on though. That is what I want to do with the next builds. I have been doing the dual boot on one HD and wine. 
The video editing is just basic editing in movie maker or something,  I upload from a camera or something. Then burn it to a dvd or save to my NAS server. I did not know Linux has better support for intel than amd. That is good to know.  Now that you mention the video problem, I think I had that issue a few years back. I removed the card and used the on board graphics and it work fine. 

Thank you

---

### Post by farrinux on 2014-08-09
Using two different HD's is how I dual boot.  I learned it from one of the admins here.  Saves a lot of frustration.  Just make sure you install Win first then Ubuntu. When installing Ubuntu make sure you put Grub on your Ubuntu hard drive and not the Win hard drive.

---

### Post by Mrdx on 2014-08-09
Thank you Farrinux. That is good advice I will use.

---

