---
title: "Will there be a benefit to reformatting usb drive to ext3?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-07-18
Lets say I have a flash drive that will only be used on Linux computers.  Would I see any benefit if I reformatted it to ext3? (from FAT32)  And if I where to do so, how would I get back the auto-mount feature to /media/XXX provided by gnome-volume-manager?

Thanks!

---

### Post by bodhi.zazen on 2008-07-18
> **pi.boy.travis said:**
> Lets say I have a flash drive that will only be used on Linux computers.  Would I see any benefit if I reformatted it to ext3? (from FAT32)  And if I where to do so, how would I get back the auto-mount feature to /media/XXX provided by gnome-volume-manager?

Thanks!

In general, yes if you are using linux only I advise a linux native file system.

The reason is more of a "what if" the file system becomes corrupt. IMO linux does not have very good tools to defragment or repair FAT or NTFS file systems.

Depending on the size of your flash drive you *might* consider Ext2

---

### Post by Jim! on 2008-07-18
If your going to be saving files that you need to be able to open up on Windows PC's as well then I wouldn't advise it, Winodows will read it as an unformatted drive. But If it's only going to be used on computers running linux then by all means format it to Ext3.

---

### Post by pi.boy.travis on 2008-07-18
Thats what I thought.

If I reformat a partition using GParted, gnome-volume-manager doesn't mount the drive to /media/whatever when it is connected anymore.  I don't really want to enter the drive in fstab. (or do I?) Is there another way to have it mounted automatically when connected?

ext3 also yields a lost+found file.  Is this normal?

---

### Post by t0p on 2008-07-18
When I recently scraped Windoze off my computer, I decided to reformat my USB stick as ext3.  So I reformatted with gparted, and found I could no longer use the stick!  So I reformatted it fat, and all was well again.

This drama may have been down to my ignorance of how to use gparted.  But I figured I'd throw in my 2 cents anyway.

---

