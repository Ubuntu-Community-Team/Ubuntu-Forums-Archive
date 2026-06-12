---
title: "Deleted What I Believe to be my Grub Partition"
date: 2018-09-13
forum: New to Ubuntu
---

### Post by ochism on 2018-09-13
Deleted What I Believe to be my Grub Partition and I can no longer boot into the Grub Loader I had and now I have no idea how to fix it. I used boot repair, which made this pastebin [http://paste.ubuntu.com/p/82J4Qjq8Wk/](http://paste.ubuntu.com/p/82J4Qjq8Wk/) . sda3 is the ubuntu partiiton but I wanted/had it dual booted so I could access the windows partition on sdb.

---

### Post by oldfred on 2018-09-13
Grub does not have a partition, but did you install with a separate /boot partition that has kernels & part of grub?
With desktops default install does not use use a /boot partition. Some servers or LVM with full drive encryption may need a separate /boot.
If that is all that is missing, you can use Boot-Repair's advance option to fulling reinstall all of grub, also check to install new kernel and install grub boot loader to MBR of sda, not to a partition.

It looks like you have a newer UEFI system, but have both Windows & Ubuntu in BIOS boot mode using MBR partitioning. Windows requires MBR for BIOS boot, but Ubuntu can use newer gpt with BIOS or UEFI if correct supporting partition is on gpt drive.

You also should be able to directly boot Windows by choosing to boot sdb drive directly from BIOS.
Windows 10 has fast start up which prevents grub from booting Windows. Boot-Repair says the NTFS is in unsafe condition which could be fast start up or that it needs chkdsk or both.
Windows, with updates, will turn fast start up back on, and then you cannot boot from grub, only directy. Best to have Windows repair flash drive as direct booting and f8 to get into internal repair console does not always work. And you cannot fix most Windows issues from Linux.

---

### Post by ochism on 2018-09-14
That seems likely, the goal was to dual boot it without having to F2 into the bios to switch over. I probably followed the standard windows 10/ Ubuntu dual boot guide. 

Opening up boot repair on by USB Ubuntu drive doesn't give the option to reinstall of of grub, the grub tabs are grayed out and empty. 
Also running boot repair the first time I think made it impossible/difficult to reach the repair console. 
I can boot into windows by using the bios so I'm not down a computer which is nice, but I had the ubuntu portion set up to do development and would prefer to not have to reinstall it.

I'm not sure about the UEFI/BIOS boot mode thing, is changing both of them to UEFI help?
And yep fast startup got reset by a windows update, although it doesn't seem to have fixed the issues. 
I also ran chkdsk, it didn't find any issues

---

### Post by oldfred on 2018-09-14
You would have to totally reinstall Windows. While I prefer UEFI, many still like the old BIOS.
Probably not worth the hassle of backing up (which you should do anyway) and then total reinstall of Windows & Ubuntu.

With Boot-Repair you need to boot Ubuntu installer in BIOS mode and add Boot-Repair. Then in advanced options click on ext4 partition and see if they you can totally reinstall grub & kernel.

---

### Post by ochism on 2018-09-15
So i figured out, after a lot of playing around with lots of things, that the partition I deleted was the root partition. I had forgotten how I had partitioned the linux portion, with a seperate home partition.

---

