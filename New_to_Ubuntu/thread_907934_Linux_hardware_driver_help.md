---
title: "Linux hardware driver help"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by jedispy on 2008-09-02
Hello everyone.
Although this may appear to be more of a hardware question than a Linux question, it'll circle around.  I'm trying to build a server out of the following:[list][*]AMD Athlon 1GHZ CPU
[*]1GB RAM
[*]ASUS a7v133 motherboard (BIOS version 1004)
[*]initio inic1620 s-ata adapter (PCI into the motherboard)
[*]Maxtor Basics SATA II/300 1TB HDD[/list]
I want to install Linux on it.  My issue is that my installation doesn't detect the hard drive.  At first I thought this was just a Linux thing, but it's happening with Windows and BSD installers too.

The issue appears to surround the fact that I don't have a Linux driver for the initio inic1620.  I tried to search but found nothing.  Does anyone know if there are any Linux drivers for this device?  Any other suggestions?

Your help is GREATLY appreciated.

---

### Post by alienexplorers on 2008-09-02
Try reading this page:
[http://www.initio.com/support/index-download.htm]("http://www.initio.com/support/index-download.htm")

---

### Post by jedispy on 2008-09-02
Wow...how did I miss that?

The solution is interesting, but I'm not entirely sure how to implement it.  I get the whole part about compiling it and what not.  The issue is that *I currently have no OS on the computer*.  What I want to do is run the OS from my SATA HDD.  However OS installers aren't detecting the drive.  The SATA controller owner's manual specifically mentions Windows 2000/XP/2003.  It also says to put the drivers for those OS versions onto a floppy disk and install via DOS.  Of course ideally what I would like is to do the same with the Linux driver via sh or bash command prompt.

Pardon my inexperience, but is it at all possible to install the Linux kernel on an IDE HDD, and add the SATA HDD as a second drive for file storage?  I know in Windows that would be like adding a "D drive" to the "C drive" (yeah I know Linux doesn't use drive letters).

---

