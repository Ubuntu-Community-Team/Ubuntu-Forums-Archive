---
title: "Problems using external HDD!!!"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by bigeyedfish on 2008-11-17
Hello...

I am new to Linux outside of whitebox command line in my classes at school.  I was having troubles with Vista and decided to restore my pc and come to linux.  

I have ubuntu 8.10.

I am trying to get into my external hdd so I can get the files off of it (mostly all music) back onto my internal hdd.

When I plug the hdd into a usb port, nothing happens on my pc but my hdd lights up as normal.

But, when I plug a flashdrive into a usb port... Ubuntu recognizes it and opens up the containing folder.

What do I need to do to make this happen with my external hdd as well?  This is important since I have over 1500 songs that I really don't feel like downloading again as well as some pictures that I don't want to lose either.

All help is appreciated, and apologies for my lack of knowledge!

Thank you in advance!

---

### Post by tomtom1982 on 2008-11-17
Please plug your external HDD on, open a terminal and write fdisk -l. Please post the message you´ll getting than.

---

### Post by bigeyedfish on 2008-11-17
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69afd9f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

----------------------------------------------------------------------------

This would be what I receive when I run that command

---

### Post by bumanie on 2008-11-17
fdisk -l is only showing your ubuntu installation - your external drive does not seem to be recognized. What filesystem does the external drive have on it?

---

### Post by bigeyedfish on 2008-11-17
Ok... well, I think I figured it out.  I grabbed my girlfriend's lappy and plugged my harddrive into it to find out that the hdd isn't showing up there either. I believe it is a corrupted hdd.

Thank you for your time folks.  Oh... and... expect some other really dumb questions from this guy in the near future!

---

### Post by bobnutfield on 2008-11-17
> **bigeyedfish said:**
> Ok... well, I think I figured it out.  I grabbed my girlfriend's lappy and plugged my harddrive into it to find out that the hdd isn't showing up there either. I believe it is a corrupted hdd.

Thank you for your time folks.  Oh... and... expect some other really dumb questions from this guy in the near future!

There are NO dumb questions.  That is what this forum is all about.

You might try to see if it show up in Gparted.  Gparted is a GUI partitioner and formatter and is very good at finding otherwise missing drives.

---

### Post by jnorthr on 2008-11-17
i'd be interested to see if your external HDD ever worked under ubuntu. How did you originally get the music onto it ? Did you use a windows machine ? Your HDD must have been formatted and depending on that format (FAT32,NTFS,ext3) will decide how we can get your music,etc. off of it.

If it's in a format that's not know to ubuntu, then we might need to do some tricks to make it 'visible' :)

---

### Post by Kenth Soderstrom on 2008-11-17
I'm running Ubuntu 8.10 and could get my external HDD to run, but when I removed that and inserted the USB from my digital camera nothing happened. I opened the filemanager, could see the USB sign but nothing happened when I doubleclicked on it. I also tried to open F-spot, import, but it said that there was no camera connected. Do I have to make some changes in the settings somewhere to access the pic's in my camera?

Kenth Söderström

---

