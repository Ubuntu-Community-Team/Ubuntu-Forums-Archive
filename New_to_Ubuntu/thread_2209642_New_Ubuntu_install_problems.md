---
title: "New Ubuntu install problems"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by Pete_Hepple on 2014-03-06
Hi,
I'm a newbie  (on Ubuntu!). Some problems : Using Win XP + SP3, Laptop.I've 2 hard disks both with 2 partitions. Main disk (C:) is Win XP, Its partition (D:) is a system backup.
The USB disk is (E:) - system backups and (F:) -  Data (archives of data etc).
[1] When I installed Ubuntu it created space between E: and F: - why ?
[2] The loader startup menu has 2 occurences of Ubuntu and 2 occurences of Win XP - why ?
[3] As the boot loader has been replaced by Ubuntu what happens if I need to uninstall Ubuntu ?
[4] There are no menu bars in Firefox - can I get them ?
Hope you can help
Thanks
Pete

---

### Post by Mark Phelps on 2014-03-06
> [1] When I installed Ubuntu it created space between E: and F: - why ?
Unlike Windows, which uses drive letters, Linux does not use them -- so it can't be installed into an existing Windows filesystem partition.  The installer created its own partition, using the Linux filesystem.
> [2] The loader startup menu has 2 occurences of Ubuntu and 2 occurences of Win XP - why ?
The startup menu creates an entry for "normal" boot and a second entry for "recovery" boot -- in case you need to repair something.  As to the Windows entries, the installation process uses something known as os_prober, which looks for signs of existing OSs on the drive.  It sees both loader files and OS files as that evidence, and will create an entry for each Windows filesystem partition it finds that contains signs of an OS.  For example, if you have the Windows loader files in one partition and the OS files in another, it will create two entries -- one for each partition.
> [3] As the boot loader has been replaced by Ubuntu what happens if I need to uninstall Ubuntu ?
Actually no, the boot loader has not been replaced; instead, the MBR has been modified to point to the partition containing the Linux boot loader.  The Windows boot loader must reside in a Windows filesystem partition and is likely, still there.  However, if you uninstall Ubuntu, you will be left with the MBR still pointing to the Ubuntu partition and it will then fail.  SO, before you do that, you would want to rewrite the MBR to point to the Windows boot loader partition.
> [4] There are no menu bars in Firefox - can I get them ?
No -- this is how the Unity desktop works -- global menu bar at the top of the screen.

---

