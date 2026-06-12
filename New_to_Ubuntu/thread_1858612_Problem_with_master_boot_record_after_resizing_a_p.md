---
title: "Problem with master boot record after resizing a partiton"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by blackind on 2011-10-12
Hi, I need some help fixing my mbr, so that I can have dual boot. After resizing my windows partition I can't boot to my Windows 7 partition. I tried various solutions on the internet and none of them worked. The problem is that I can't access the windows partition from Ubuntu either.

I tried:

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d9a40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6397    51378176   83  Linux
/dev/sda2   *        6397       16020    77296640    7  HPFS/NTFS
/dev/sda3           16020       25807    78613504    b  W95 FAT32
/dev/sda4           25807       38914   105278465    5  Extended
/dev/sda5           25807       26415     4881408   82  Linux swap / Solaris
/dev/sda6           26415       38914   100396032   83  Linux


but the gparted doesn't recognise the file system:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204117&stc=1&d=1318451011[/IMG]


Any ideas are welcome,

Thx

---

### Post by Basher101 on 2011-10-12
i think i have bad, bad news for you...but before that, HOW did you resize it? give exact details to how you made the process

---

### Post by blackind on 2011-10-12
As it was about a month ago I don't remember, I think the last thing I tried was:

sudo ms-sys -m /dev/sda2

---

### Post by Mark Phelps on 2011-10-12
You're PRESUMING your MBR is the problem -- it's most likely NOT the problem at all.

If only your MBR was corrupted, then the GParted screenshot would have shown a "normal" NTFS partition where Windows used to be.

You've told us what doesn't work -- but you've not given us any info as to what DOES happen when you do various things.

So, in addition to HOW you resized your Windows partition, we need to know the following:
1) What do you see when you boot the PC?  IF you're not getting a GRUB menu, then next time when you reboot, hold down a SHIFT key.  That should force a GRUB menu.  IF you then see that menu, GRUB is working.
2) What solutions did you try and what happened for each? There's no point in us trying to guess what will still NOT work -- if you already tried something and it failed.
3) HOW are you trying to access the Windows partition in Ubuntu? And what is happening when you do that?

---

### Post by blackind on 2011-10-12
About the resize, I used gparted, I increased the size of my 1st partition for linux, and reduced my windows. I remember having access from ubuntu to the windows partiton after that, but not being able to boot to windows

---

### Post by blackind on 2011-10-12
So, after trying ms-sys, I boot from a live Ubuntu cd, and I reinstalled the Ubuntu, defining a mount point for each partition, for ntfs partition I defined /windows as the mount point.

By the way, grub is installed, I have the option to boot to Ubuntu of windows 7. 

When I try to boot to windows I have the following message:

error no such device 80DCE7C0DCE7AE9A
Missing operating System
Operating System not found.

When I boot to ubuntu I get this message:

The disk drive for windows is not ready yet or not present.
Continue to wait, skip or manual recovery. 
I skip and boot to linux

---

### Post by Basher101 on 2011-10-12
you corrupted your windows partition. the only thing you can do now is wipe it, make it NTFS and reinstall windows 7 from scratch. all your data is a goner.

---

### Post by blackind on 2011-10-12
So, bad news! Thx...

---

### Post by Mark Phelps on 2011-10-13
While using GParted to shrink Win7 OS partitions has a history of corrupting the partition and rendering Win7 unbootable as a result, it's usually an easy fix by booting from a Win7 Repair CD and running Startup Repair at least three times.

However, that would not explain the other problems you're seeing.

If you want to try that, you need to go to the link below and purchase the proper Win7 boot image, download that image, burn it to CD, boot from it, and run Startup Repair at least three times:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

