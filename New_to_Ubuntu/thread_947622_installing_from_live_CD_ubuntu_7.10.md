---
title: "installing from live CD ubuntu 7.10"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by enigmaingr on 2008-10-14
Hello,

I'm attempting to install Ubuntu 7.10 from a live CD onto a system with no OS.  The CD boots fine.  When I try installing, I can't get past Step 4, which deals with partioning the hard drive.  Nothing shows up in the gparted window; the HDD is not found by ubuntu although it is in BIOS.  

What I have attempted so far:

-I tried installing from all six (or seven) options from the main menu of the CD.  
-Internet works fine
-I checked the CD for quality (it's good)
-I tried downloading a new ISO (for 8.04) but it stopped halfway through, saying that there is not enough space.  For some reason, it's thinking there is only 460+ MB of space left.  
-the boot order is set to the configuration suggested on all the forums
-I only have one HDD and I'd like to dedicate it all to Ubuntu.  
-I can't mount any of the first two things that show under "computer"; it says I don't have permissions.  
-to emphasis, the live CD works fine each and every time I try but I can't get past Step 4 in the install process.

---

### Post by overdrank on 2008-10-14
> **enigmaingr said:**
> Hello,

I'm attempting to install Ubuntu 7.10 from a live CD onto a system with no OS.  The CD boots fine.  When I try installing, I can't get past Step 4, which deals with partioning the hard drive.  Nothing shows up in the gparted window; the HDD is not found by ubuntu although it is in BIOS.  

What I have attempted so far:

-I tried installing from all six (or seven) options from the main menu of the CD.  
-Internet works fine
-I checked the CD for quality (it's good)
-I tried downloading a new ISO (for 8.04) but it stopped halfway through, saying that there is not enough space.  For some reason, it's thinking there is only 460+ MB of space left.  
-the boot order is set to the configuration suggested on all the forums
-I only have one HDD and I'd like to dedicate it all to Ubuntu.  
-I can't mount any of the first two things that show under "computer"; it says I don't have permissions.  
-to emphasis, the live CD works fine each and every time I try but I can't get past Step 4 in the install process.

Hi and wlecome, could you give us some system specs?
Moved to ABT :)

---

### Post by bobnutfield on 2008-10-14
When running the live cd, does opening a terminal and typing:

> sudo fdisk -l

yeild any results?

---

### Post by LowSky on 2008-10-14
[QUOTE=enigmaingr;5964396]Hello,
What I have attempted so far....
-I tried downloading a new ISO (for 8.04) but it stopped halfway through, saying that there is not enough space....  For some reason, it's thinking there is only 460+ MB of space left....  
-the boot order is set to the configuration suggested on all the forums
-I only have one HDD and I'd like to dedicate it all to Ubuntu.  
-QUOTE]

OK first off the liveCD run only on your RAM, it will not use you hard drive at all, that why you cant download the newer version from a LIVECD session, there is nowhere to put it.

try to acces the drive with the live CD with Gparted (will be called partiton editor in the menu (under system)

if that doesn't work you can creat a Gparted Live CD from here,[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by enigmaingr on 2008-10-14
Thank you all!  Here are the system specs:

HP d530 CMT (DG768A)
Pentium 4 2666MHz
Speed: 2666/533MHz
Stepping: F27
Cache Size (L1/L2): 20/512 KB
Memory: 1024 MB DDR/333 MHz/Dual Channel
System BIOS: 786B2 v.1.10
Hard Drive: IDE Primary 0 120GB WDC WD 1200JB 00GVA0

---

### Post by enigmaingr on 2008-10-14
In addition, I just downloaded a live CD of the newest ubuntu version.  Same problem: When installing, I get to step 4.  The error reads: "No root file system is defined".  I try Gparted and nothing appears.

Last edit/update:

Okay, so I downloaded Gparted live CD.  It found the hard drive and I formatted to FAT32 with it.  Unfortunately, I still cannot install ubuntu because the live CD's Gparted still doesn't see it.  Any suggestions?

Latest update: I'm guessing that I need to know how to mount, or transport, settings found and made in Gparted live CD to either my HD or the Ubuntu live CD.  After finding and formatting the drive in the Gparted live CD, I still cannot find it either through the Ubuntu live CD or the alternative install live CD.

In Addition: Tried installing with the alternate live CD.  It still can't find the HD.  The next screen asks me to select a driver.  I chose the "all_generic_ide" one.  Still nothing.

---

### Post by enigmaingr on 2008-10-15
> **bobnutfield said:**
> When running the live cd, does opening a terminal and typing:



yeild any results?
fdisk returns nothing, just the prompt

---

### Post by bobnutfield on 2008-10-15
Since you have been able to format your hard drive with the Live Gparted CD, try formatting again and this time format to the ext3 file system.  I don't know if that is going to solve the problem, but that is the filesystem that Ubuntu will use when you do install.

---

### Post by enigmaingr on 2008-10-15
> **bobnutfield said:**
> Since you have been able to format your hard drive with the Live Gparted CD, try formatting again and this time format to the ext3 file system.  I don't know if that is going to solve the problem, but that is the filesystem that Ubuntu will use when you do install.

Thanks!  I will try this.  I'm hoping this works.  It has been a sleepless, but exciting 48 hours.  New to ubuntu but excited to learn.

Update:  Unfortunately, this didn't work.  When trying to install, nothing is found in step 4.

Update 2: I reformatted and repartitioned through Gparted live CD so that there were no unassigned parts.  Upon starting the ubuntu live CD, I went to options and checked the "acpi=off" and "noacpi" options.  Still not able to get past Step 4.

---

### Post by bobnutfield on 2008-10-15
Persevere and you will eventually win!

---

### Post by enigmaingr on 2008-10-16
I did it!  I'm officially into ubuntu!  

For future reference to all those who may deal with a similar issue, this is all I had to do:

-open the case and look at the hard drive.
-on the back, you'll see an area of about 10 little pins and (hopefully) a little white thing covering two of them.  
-if you look real close, you'll see the letters 'M', 'S', and 'C'
-you need to ensure the white thing covers the pins that coordinate with 'S'.
-I'm told this designates the drive as "slave"
-When you boot-up, you should now see the hard drive as "IDE primary 1"

Once again, my issue was my Western Digital WD1200JB hard drive wasn't seen by the install disk.

---

