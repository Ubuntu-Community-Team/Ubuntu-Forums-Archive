---
title: "[SOLVED] 8.10  USB stick booting problems - wierd"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by candtalan on 2008-11-06
Using the live CD of 8.10, I make a bootable USB stick using a 1gb usb.
It appears to create ok.

I then use the usb stick to boot the machine, and - it works - in the desktop machine I created the usb in - as it happens.

However, I try the live usb stick in my asus 900 eeepc and do the usual thing - initially select the usb for booting - and I then see an error message 
'error loading operating system'

I also try the same usb stick in a dell laptop - Inspiron 1100 - and get the same error.

I look at the usb stick  with a partition editor and it is marked as boot (whatever that means).

Both the machines - eeepc and the inspiron 1100 each boot perfectly well from another usb stick (using 8.04.1 and created independently)

Any ideas please?

UPDATE:
I have repeated this process, and the error, after using another desktop of different type to create the bootable usb stick while running the live cd.
It looks like there live cd facility for creation of live usb stick is suspect. I have not yet tried it after a 8.10 install, then making a live usb stick. Maybe some updates after the cd install will make a difference?
I also have not yet tried another usb stick, maybe that is a problem(?)

---

### Post by C.S.Cameron on 2008-11-06
After dozens of installs with usb-creator, (some worked many did not), I am starting to think this has something to do with the formatting of the flash drive.
For example:
Had U-C install working on 2G Kingston.
Used EEE PC support DVD to make EEE recovery disk, (this formatted the drive).
Reformatted flash drive, (using gparted CD).
Installed 8.10 from CD using U-C.
Got Error 17, (not grub error 17).
Deleted files and used Unibootin to install 8.10, (this worked).
Deleted files and used U-C to install 8.10, (this worked).
Reformatted with gparted installed using U-C and it still worked.
Have also tried this on 4G Kingston with same results.

---

### Post by candtalan on 2008-11-06
Interesting.
I have just tried using Unetbootin (in kubuntu) and the usb bootable stick with 8.10 ubuntu on ot works fine, (with the limitation of not offering the live cd boot menu - I need safe graphics on one laptop).

I did however notice that Unetbootin required a fat32 format whereas the ubuntu live usb facility seems to create only a fat16 partition. 

Does this relate to your comment about formatting somehow?

---

### Post by C.S.Cameron on 2008-11-06
At the moment I have an install from the ubuntu live usb facility working with a FAT32 partition.
I am wondering, if you erase the Unetbootin created files and reinstall to the same partition using the live usb facility, if it will work.
(not letting usb-creator format the disk).

---

### Post by candtalan on 2008-11-07
From what I have seen here, even if you let U-C do a format, it will still work - on the condition that you begin with a fat32 partition (before U-C does a format), and it will still work.

My guess so far is that something only works properly with a fat32 (syslinux, or something in the configuartion maybe??) and that U-C does not force a format. i am not sure even that U-C format would do a fat32 format when initially offered a fat16 stick. Needs to be proved yet.

In my cases here I made no special effort to do a format at all in my early experiments I think. I may have left the sticks as their original fat16 and I certainly deleted files when U-C told me the stick was too full to start.

Later I used gparted to format to fat32 and it all worked. Also after it was fat32,I then used a U-C 'format' and it appeared to do a format, and it still worked ok, and the stick was still fat32. So presumably U-C format in this case was in fact fat32. I have not done a test to see if, when I offer U-C a stick which is fat16, then its format actually formats to fat32 as one might expect.

I am fairly sure that one way or another, it all only works if the stick is fat32.

---

### Post by louis0591 on 2009-03-31
i am having the same prob. i have a one gig stick, formatted to fat32 (using gparted).  i then used the tool in ubuntu 8.10 to create my live usb. after it transfers files it says its ok use but when i try i either get "boot error" or "boot error no operating system". 

someone please help me cuz im trying to install ubuntu on my hp mini mi netbook and i need to do it through the usb.

---

