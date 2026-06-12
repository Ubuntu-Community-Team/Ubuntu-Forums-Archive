---
title: "problems with partitions and windows"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by shiftygod on 2013-07-16
i installed ubuntu and have tried to create a partition to re install windows i was unsuccessful and was not able too so i decided to just install windows wiping ubuntu then reinstalling ubuntu alongside windows. when i came to installing windows i could not. it said that partition was not the right format or something like that so now im stuck with ubuntu and cannot play games. any help?

i will always want ubuntu installed but i need windows for games!

---

### Post by Impavidus on 2013-07-16
Boot Ubuntu from your live disk (the one you used for installing it), resize your Ubuntu partition and create an NTFS partition of sufficient size. It has to be a primary partition. Windows should be able to install on that. This will leave Ubuntu unreachable because the Windows installer overwrites the boot loader, but you can fix this from your live disk using [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair").

As you just installed there are no valuable files on the hard drive, so you don't have to make backups.

---

### Post by Mark Phelps on 2013-07-16
When you go to reinstall Windows, in the installer, reformat the NTFS partition.  Windows works best when it formats its own partitions.

---

### Post by shiftygod on 2013-07-16
iv tried messing with the partitions but i cannot change anything on the partition apart from the flags.

---

### Post by mastablasta on 2013-07-16
you need to boot into **live session** and use gparted to handle partitions. you might need to run it with 
```
gksu gparted

```you can also erase the whole disk (make it unformatted) that will also help windows to find the disk.

---

### Post by oldfred on 2013-07-16
Did you use all 4 primary partitions for Linux? Generally better to have Linux or some of the Linux formatted partitions as logical partitions in the extended partition and let Windows have the primary partition that it needs.
It needs primary sda1 thru sda4, formatted NTFS, with the boot flag to install into.

---

### Post by shiftygod on 2013-07-16
what does this code do? and what is live session?

---

### Post by shiftygod on 2013-07-16
GParted shows that i have 3 partitons,
/dev/sda1, filesystems is ext4 mount / flagged with boot
/dev/sda2, filesystem extended
/dev/sda5, silesystems linux-swap

hope this helps at all

---

### Post by oldfred on 2013-07-16
Shrink sda1. Make a new sda2 and format it NTFS. Move boot flag from sda1 to sda2. Then Windows should install. Some have had to use the Windows installer or Windows command line to reformat and make active the NTFS partition. I think gparted creates XP type NTFS and Windows 7 should just install to that, but sometimes it complains.

---

