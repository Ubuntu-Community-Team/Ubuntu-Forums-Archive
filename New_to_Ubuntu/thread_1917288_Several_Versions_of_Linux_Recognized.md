---
title: "Several Versions of Linux Recognized"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by chris1216 on 2012-01-29
All,


I have installed several versions of Ubuntu and other Linux distributions over the past several months in an attempt to find one that suited me.  I have not found the "one" for me yet, but I am having fun.  My question is, I have installed all of these on the same partition in a dual boot with Windows 7 Starter, and now at startup the system recognizes about three versions of Ubuntu and several other distros in addition to Windows 7.  Does anyone have any thoughts on how to totally overwrite this partition so only the version of Linux I am currently running shows up?

I thought I was correctly using Gparted to do this, but apparently not.  I also recently read Knoppix Hacks, and I recall a shred command, although I cannot remember if it would work on a partition.


Chris

---

### Post by dixonstalbert on 2012-01-29
Hi chris

I am not sure how you can install more than one operating system on one partition.
In Ubuntu, can you run 

System > Administration > Disk Utility 

and confirm your harddrive partitions.


(This is a totally safe way of getting a partition map of your harddrive.)

post back if you find more than one partition on your harddrive.

---

### Post by chris1216 on 2012-01-29
Well, I never had more than one at a time on this partition.  And if I read this correctly I show three primary and one extended.  The extended is where I put Ubuntu and the associated SWAP file.

---

### Post by dixonstalbert on 2012-01-29
If you have just one linux partition, then probably what you are seeing is separate normal and recovery entries for each of the linux kernels that are installed. When you update your kernel it leaves the old in place and adds a new grub menu entry for the new one. After a few months you can end up with a dozen entries. 

It is safest just to leave the old kernels in place since modern harddrives have tons of space. They will not slow down your system and if you delete the wrong one you will have troubles.

You can search the forums on "Grub2 Advanced" to get the excellent tutorial about how to simplify grub menu so it just shows your most current linux install and windows.

Or, you can search forums for "Grub Customizer" which is a little app that gives you a nice gui to edit your grub menu.

hope this helps

---

### Post by ajgreeny on 2012-01-29
Let's see the output of ```
sudo fdisk -l
```lower case L at the end.

---

### Post by chris1216 on 2012-01-29
Ajgreeny, Here is what it showed:

isk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x460bfc27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6291456   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         784         797      102400   27  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3             797       11568    86521114    7  HPFS/NTFS
/dev/sda4           11568       19458    63373313    5  Extended
/dev/sda5           11568       19130    60742656   83  Linux
/dev/sda6           19130       19458     2629632   82  Linux swap / Solaris
chris@chris-netbook:~$

---

### Post by dixonstalbert on 2012-01-29
Your fdisk -l output indeed shows only one linux partition 

ajgreeny's signature has correct link "Grub2 Basics" (sorry I thought it was the 'advanced' one) to forum post about how to get rid of unwanted grub menu items.

---

### Post by chris1216 on 2012-01-29
Thanks. I will read up on that and post my progress.

---

### Post by chris1216 on 2012-01-29
I downloaded and used the Grub-Customizer.  I "un-ticked" what I did not want displayed and when I re-booted the unwanted entries were gone.  I tried to play with adding a picture and changing the color of the font, but was unable to get that to work.

I am marking this as solved as my original question was answered.  Thanks for your help.

---

