---
title: "Hardware &amp; Dual Boot Questions"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by bpalone on 2008-06-15
I have already set one machine up as a Dual Boot and will be setting up my laptop as a dual boot after I do a hard drive upgrade.  But, I have a main computer that has me a bit worried about messing up things.  Below are the pertinent hardware items, a statement of what I want to do, and then my questions.  Be easy on me, I’m not a total noob, but close to it.

Hardware:

ASUS A8V MB
1gig memory
AMD Athlon 64 2.0 Ghz

Two (2) 160 gig hd set up as Raid 1

VIA Serial ATA RAID Controller (VIA VT6420 (VT8237) SATA RAID) 

3DForce MX4000, NVIDIA GeForced dual monitor video card


Here is what I want to do:

Install an IDE HD back into machine to hold UBUNTU and associated files, while leaving the existing RAID 1 in tact with my old Windows still there.  To make machine dual boot.


My questions:

1.) Does, or has, anyone have experience with UBUNTU and the aforementioned RAID hardware?  ASUS doesn’t offer a Linux driver for the VIA chipset (and I haven’t done a Google yet).  My concern is missing up my data on the existing Raid 1 disks.  Many, many dollars worth of data and I want to be able to access it from UBUNTU as well as the Windows OS.

2.) Anyone have experience good or bad with the dual monitor video card recited above?  From a quick look, I believe I can get it to work without to much trouble.  The live CD does drive one of the two monitors, while making the second very obnoxious.  That is the reason I believe I can tweak and get it to work from what I have read.

I am sick of the NT Bloat and the NT Call Home, so I am going to try to move most of my activities to Linux OS.  I can’t leave entirely, but I can get 80% to 95% moved and may even be able to do better, but I doubt it as I have an old Plotter that I didn’t have much luck in locating a driver for Linux.  So, I am stuck with Dual Boot in order to continue in business, especially since virtualization doesn’t do well on the print side when a Windows Printer Driver is all that is available.

Thanks in advance and I apologize for the length of this.

---

### Post by ebmelle on 2008-06-15
In ubuntu 8.04 you can install as an application in a Windows type FAT32 'folder'. If you go that route the installer will create a 20GB 'folder' into which it will install all the ubuntu files. The result is a dual boot setup, with all the Windows data available and visible to ubuntu.  Some disk access speed is said to be sacrificed due to the FAT32 partition type. ---  Works great on this acer notebook.

---

### Post by bpalone on 2008-06-16
Dual Booting and access to the data is not my question.  My question is retaining my RAID 1 Array while in Linux.  What has been anyones experience with this?  From I have found on line, it appears that I will have to sacrifice the RAID Array.  Would like to find something to the contrary, but I am a big kid and can adjust if need be.

I am even open to other alternatives to keep the array going and valid.  It would just need to be active on BOTH OSes.

Thanks again in advance.

---

