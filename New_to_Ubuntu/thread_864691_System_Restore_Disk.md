---
title: "System Restore Disk"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Shippou on 2008-07-19
How can I create one? I want to give Kubuntu Hardy another shot, but then i want to create a backup disk so that when Hardy fails me again, I can get back my previous installation, complete with the installed updates and programs.

Thanks for the help.

---

### Post by unutbu on 2008-07-19
Do you have 10GB of free disk space? If so, the safest way to install a new OS is to create a new partition and install the OS there.

---

### Post by Shippou on 2008-07-19
Well, that is one way.

But I am really interested on how to create a system restore disk, somewhat what like Windows uses.

and to be able to restore your computer's configuration from them.

---

### Post by stmiller on 2008-07-20
There is not really an easy way to do this. Here are a couple of options:

[http://www.improvedsource.com/view.php/Linux-System/18](http://www.improvedsource.com/view.php/Linux-System/18)

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)


You could also use clonezilla (a live CD) to clone your hard drive to another hard drive.

---

### Post by bsell on 2008-07-21
> **Shippou said:**
> How can I create one? I want to give Kubuntu Hardy another shot, but then i want to create a backup disk so that when Hardy fails me again, I can get back my previous installation, complete with the installed updates and programs.

Thanks for the help.

[Partimage]("http://www.partimage.org/Main_Page")

> **Description:** Partimage is a Linux utility which saves partitions having a [**supported filesystem**]("http://www.partimage.org/Supported-Filesystems") to an image file. Most Linux and Windows filesystems are supported. The image file can be compressed with the gzip / bzip2 programs to save disk space, and they can be splitted into multiple files to be copied on CDs / DVDs, ... Partitions can also be [**saved across the network**]("http://www.partimage.org/Partimage-manual_Network-support") since version 0.6.0 using the partimage network support, or using Samba / NFS. If you don't want to install Partimage, you can download and burn [**SystemRescueCd**]("http://www.sysresccd.org/"). It's a livecd that allows to use Partimage immediately even if your computer has no operating system installed (useful to restore an image), and it allows to [**save an image on a DVD on the fly**]("http://www.sysresccd.org/Sysresccd-manual-en_Burning_a_DVD_RW_from_SystemRescueCd_by_mounting_it"). 

---

### Post by ktrnka on 2008-07-21
You might be interested in remastersys

[http://www.remastersys.klikit-linux.com/]("http://www.remastersys.klikit-linux.com/")

---

