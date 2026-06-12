---
title: "Different partitions in ubuntu"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by bandelguy on 2011-10-20
I want to install ubuntu on a new hard disk. The following are some of my queries: 1. If i want to separate partitions just like in windows, i need to create extended partition and in it logical partitions ?  2. Do these partitions automatically show up at startup or do I have to mount them like ntfs partitions?

---

### Post by Elfy on 2011-10-20
You don't HAVE to use extended partition and logicals - I prefer to so I can add and move as I wish.

The only partitions that automatically show at boot are those in fstab - you'd need to add any extra ones you create.

---

### Post by satanselbow on 2011-10-20
> **bandelguy said:**
> 1. If i want to separate partitions just like in windows, i need to create extended partition and in it logical partitions ?


You are most likely only having to create extended-> logical partitions in windows as you machine have already used up the max 4 allowable PRIMARY partitions. Sometimes like this:

Primary 1 - 100MB created at windows installation
Primary 2 - "Main" windows installation
Primary 3 - Windows Recovery Enviroment
Primary 4 - OEM / Manufacturer disk image for use by recovery 

This really is not good...

If you are installing onto a "New" harddrive AND NOT DUAL BOOTING OFF THAT DRIVE - you can either use up all your 4 allowed primary partitions (not really a good idea) or create an extended partition and create logical partitions for your chosen Ubuntu schema ;)

Check the forum for various "recommended" partitioning schemes... there are loads of ways of doing it - some with more merit than others :D


> **bandelguy said:**
> 
2. Do these partitions automatically show up at startup or do I have to mount them like ntfs partitions?

Yes they do and no you don't ;) Any partitions you use for your new Ubu installation (ie / /boot /home etc)will mounted automatically as the OS boots.

---

### Post by oldfred on 2011-10-20
Just to throw a monkey wrench in the works, if it is a new drive and you will not install Windows you can use gpt(GUID) instead of MBR(msdos) partitioning. 

Gpt is what Macs use. Windows only can boot from it with new computers that boot with UEFI, but Win7 & Vista will read it. But Ubuntu can use gpt with BIOS boot. All partitions are primary and you need a tiny bios_grub partition, but after that there is no real difference in your system. Gpt is also required if drive is over 2TiB, but can be used on smaller drives. I installed it on a 16GB flash drive just to test it.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

