---
title: "New hard drive what file system?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Nemo0075 on 2008-11-14
Hello all,

  I bought a second hard drive so I could keep all my personal files on one drive and OS and system file on another.

  I have physically installed the drive in the system.  Checked the BIOS to make sure it sees it (it does).  Installed Gparted to format it.  I just don't know what file system I need to put on it. My dev/sda is ext 3 when I choose to create a new partition on dev/sdb it gives me msdos, aix, amiga, bsd, dvh, gpt, mac, pc98, sun and loop.  My gut tells me dvh however I have been wrong before:lolflag:

Thanks for the hep

---

### Post by SuperSonic4 on 2008-11-14
That's unusual, are you sure you can't use ext3 or ntfs? You don't need a mount point or anything.

If you want windows + linux use ntfs
linux only = ext3

---

### Post by wolfen69 on 2008-11-14
i use fat32 just to avoid any permissions problems. plus, it's universal in the sense that any OS can read it.

---

### Post by igknighted on 2008-11-14
> **SuperSonic4 said:**
> That's unusual, are you sure you can't use ext3 or ntfs? You don't need a mount point or anything.

If you want windows + linux use ntfs
linux only = ext3

For windows + linux I'd use ext3, its a more stable filesystem and if anything ever happens you have myriad free software tools to fix it, while with ntfs you need to buy proprietary windows tools to fix it.

---

### Post by Nemo0075 on 2008-11-14
Thanks guy's I figured it out.  Just needed to dig a little deeper.:)

---

### Post by jenkinbr on 2008-11-14
> **igknighted said:**
> For windows + linux I'd use ext3, its a more stable filesystem and if anything ever happens you have myriad free software tools to fix it, while with ntfs you need to buy proprietary windows tools to fix it.
So would I, but you will need a utility such as [Ext2 installible filesystem]("http://www.fs-driver.org/") for Windows to access Ubuntu's filesystem.  However, Windows DOES NOT pay any attention to ext3 permissions with this driver, so be very carful if you mount root in windows.

---

