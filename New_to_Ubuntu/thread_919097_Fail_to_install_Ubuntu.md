---
title: "Fail to install Ubuntu"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by dudeua on 2008-09-13
Hi

I'm trying to install the Ubuntu 8.04 on my machine, but fail to do it. 

First of all, I tried to install from CD. But the partiotion manager cannot detect my hardrive. It doesn't show any partition at all and all the buttons are greyed.

Next, I tried to install from Vista. After installation was completed it asked me to reboot. Now I have two options during PC boot: Vista and Ubuntu. But if I select Ubuntu, my PC just restarts. 

Can anybody tell me, what am I doing wrong? Perhaps, some links that I couldn't find? 

Thanks

---

### Post by The-Wise-Man on 2008-09-13
What kind of computer do you have? Some computers like Hp, Compaq and Dell have a "Virus Protection" setting in the BIOS. This makes it so you can't install any operating system. That could be your problem. 2nd If your computer supports it can't you just boot from the Ubuntu cd instead of using the WUBI boot feature?

---

### Post by billgoldberg on 2008-09-13
> **The-Wise-Man said:**
> What kind of computer do you have? Some computers like Hp, Compaq and Dell have a "Virus Protection" setting in the BIOS. This makes it so you can't install any operating system. That could be your problem. 2nd If your computer supports it can't you just boot from the Ubuntu cd instead of using the WUBI boot feature?

I never heard of such virus protection.

I hope you can disable that useless feature.

---

### Post by dudeua on 2008-09-13
1. The virus protection option is disabled. 
2. Sure, I can boot from ubuntu CD. As I told, the installation starts smmothly until the moment when I need to select a partition. As I understand the tool can't detect my HDD, cause it doesn't show any partion in the list.

---

### Post by dudeua on 2008-09-13
Here's the configuration of my PC:

Processor
Model : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
Speed : 1.80GHz
Performance Rating : PR6134 (estimated)
Cores per Processor : 2 Unit(s)
Threads per Core : 1 Unit(s)
Type : Dual-Core
Internal Data Cache : 2x 32kB Synchronous, Write-Thru, 8-way set, 64 byte line size
L2 On-board Cache : 1x 2MB ECC Synchronous, ATC, 8-way set, 64 byte line size, 2 threads sharing

Mainboard
Bus(es) : ISA PCI PCIe IMB USB i2c/SMBus
MP Support : 1 Processor(s)
MP APIC : Yes
System BIOS : Phoenix Technologies, LTD 6.00 PG
System : MICRO-STAR INTERNATIONAL CO., LTD MS-7235
Mainboard : MICRO-STAR INTERNATIONAL CO., LTD MS-7235
Total Memory : 2GB

Chipset 1
Model : Intel Corporation P965/G965 Memory Controller Hub
Front Side Bus Speed : 4x 200MHz (800MHz data rate)

Video System
Monitor/Panel : Generic PnP Monitor
Adapter : NVIDIA GeForce 7600 GS (Microsoft Corporation - WDDM)

Physical Storage Devices
Hard Disk : WDC WD1200JB-00GVA0 ATA Device (112GB)
CD-ROM/DVD : ASUS DRW-1608P3S ATA Device (CD 40X Rd, 40X Wr) (DVD 5X Rd, 5X Wr)
CD-ROM/DVD : TP2430G ODS935X SCSI CdRom Device (CD 32X Rd) (DVD 4X Rd)
CD-ROM/DVD : TP2430G ODS935X SCSI CdRom Device (CD 32X Rd) (DVD 4X Rd)

Logical Storage Devices
Hard Disk (C:) : 15GB (1.6GB, 11% Free Space) (NTFS)
Soft (D:) : 24GB (535MB, 2% Free Space) (NTFS)
Media (E:) : 63GB (6.8GB, 11% Free Space) (NTFS)
New Volume (F:) : 9.4GB (1.2GB, 12% Free Space) (NTFS)
CD-ROM/DVD (G:) : N/A
CD-ROM/DVD (H:) : N/A
FM2008 (I:) : 544MB (UDF)

---

### Post by The-Wise-Man on 2008-09-13
Are you trying to dual boot Vista and Ubuntu or Just Ubuntu?

---

### Post by dudeua on 2008-09-13
Dualboot.

---

### Post by The-Wise-Man on 2008-09-13
Okay, If I were you I would try and use Gparted to see if it recognizes your Hard Disk. If it does, partition it in there. Then try to run the Ubuntu installation disk again.

Gparted Download ---- [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by dudeua on 2008-09-13
I've downloaded and burned out a CD of GParted, but don't understand how to use it. After sucessfull load of Live CD it shows me the command shell. What and how should I check there?

---

### Post by kansasnoob on 2008-09-13
Give this guide a whirl:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

It suggests using Vista's own tools to "prepare" for installation, which I much prefer!

---

### Post by dudeua on 2008-09-13
Guys, thanks for your effort, but at this point I really disappointed with that distro. 

Main question, is not how to make dualboot, but how to make ubuntu (GParted) see my hdd. I can't install it on my machine at all, neither single- or dualboot. 

Googling around, I've found a command line option for installation all_generic_ide. But it also didn't help me. I'm almost sure, that the problem is caused by my motherboard handling for IDE drives. It has some feature named jMicron, which as I understand translates IDE drives to SATA. 

Concerning this additional info, can anyone suggest any further steps? 

P.S. I have successfully installed ubuntu on VMWare.

---

### Post by starcannon on 2008-09-13
If you decide to do a dual boot in the future, be sure to back up all of the files you'd not want to lose first.

An easy and safe method of "dual booting" is wubi, its located on the install disk, and is fully featured, requires no partitioning, and works excellently.

GL

---

### Post by dudeua on 2008-09-13
> **starcannon said:**
> If you decide to do a dual boot in the future, be sure to back up all of the files you'd not want to lose first.

An easy and safe method of "dual booting" is wubi, its located on the install disk, and is fully featured, requires no partitioning, and works excellently.

GL

Sure, it works smoothly, but after its work I cannot boot into ubuntu - my PC just restarts

---

### Post by matrix14 on 2008-09-13
I have a little information from some advanced programmer on my town that not able to install other OS's such Linux with dual boot nearby Windows Vista; the GRUB won't booting wheen start Linux. 
Even one of my friends as he was a senior computer technician at last deleted his Vista from his laptop due such problem.
It is hard to say that you have to choose only one OS regarding this problem between Ubuntu or Vista...

---

### Post by kansasnoob on 2008-09-13
Can you boot and run the live CD by choosing: Try Ubuntu without any change to your computer?

If so go to Terminal (under Applications > Accessories) and post the output of:

```
 sudo fdisk -l
```

---

### Post by kansasnoob on 2008-09-13
I'm gonna' go ahead and say what I'm thinking here. Looking at this:

> Logical Storage Devices
Hard Disk (C : 15GB (1.6GB, 11% Free Space) (NTFS)
Soft (D : 24GB (535MB, 2% Free Space) (NTFS)
Media (E : 63GB (6.8GB, 11% Free Space) (NTFS)
New Volume (F : 9.4GB (1.2GB, 12% Free Space) (NTFS)
CD-ROM/DVD (G : N/A
CD-ROM/DVD (H : N/A
FM2008 (I : 544MB (UDF)

I look at:

> New Volume (F : 9.4GB (1.2GB, 12% Free Space) (NTFS)

I see a horrible problem! If you're trying to create a dual boot you're using NTFS for Linux!

But, honestly it looks to me like your drive is running out of space! Especially when you consider that Windows splatters unmovable data all over a disc!

That's why I said earlier it's better to use Vista's own tools to repartition. It'll show you what you can or can't move.

---

### Post by dudeua on 2008-09-13
> **kansasnoob said:**
> Can you boot and run the live CD by choosing: Try Ubuntu without any change to your computer?

If so go to Terminal (under Applications > Accessories) and post the output of:

```
 sudo fdisk -l
```

It ouputs nothing. 
I tried to do the same with the help of parted. It also can't detect any partitions. In fact it has problems even with my dvd drive. 
The interesting part is that parted detects my dvd as /dev/scd0. And in fact it's not SATA but rather IDE. So DVD and my hard drive both are connected via single connector to the motherboard IDE slot. And I suspect that if DVD is detected as SATA drive, then the hdd must be also detected similary.

---

### Post by kansasnoob on 2008-09-13
> **dudeua said:**
> It ouputs nothing. 
I tried to do the same with the help of parted. It also can't detect any partitions. In fact it has problems even with my dvd drive. 
The interesting part is that parted detects my dvd as /dev/scd0. And in fact it's not SATA but rather IDE. So DVD and my hard drive both are connected via single connector to the motherboard IDE slot. And I suspect that if DVD is detected as SATA drive, then the hdd must be also detected similary.

Are you still running the live CD?

---

### Post by dudeua on 2008-09-13
> **kansasnoob said:**
> Are you still running the live CD?

I'm in Vista now, but can boot Live CD any moment if needed.

---

### Post by kansasnoob on 2008-09-13
Well, basically only you can know what's on this drive:

> Logical Storage Devices
Hard Disk (C : 15GB (1.6GB, 11% Free Space) (NTFS)
Soft (D : 24GB (535MB, 2% Free Space) (NTFS)
Media (E : 63GB (6.8GB, 11% Free Space) (NTFS)
New Volume (F : 9.4GB (1.2GB, 12% Free Space) (NTFS)
CD-ROM/DVD (G : N/A
CD-ROM/DVD (H : N/A
FM2008 (I : 544MB (UDF) 

I was going to suggest while you're in the live CD environment to go to System > Administration > Partition Editor so we could see if it works any different than your Gparted live CD, but it probably wouldn't matter.

Only you know what's on your drive. When was the last time you ran Cleanup or Defragged? I've freed up as much as 4GB of space cleaning out old restore points.

Then, if you know for sure that this: "New Volume (F : 9.4GB (1.2GB, 12% Free Space) (NTFS)" is where you were trying to install Ubuntu I'd delete it! BUT only if you're sure!

Then go back to that APC guide I posted before and see if Vista's own tools will do the partitioning. You only need about 8GB (I prefer 10) to install Ubuntu.

I've used that APC guide without trouble numerous times! Now, it may be that you're having trouble due to the additional partitions. It depends on how the partitions are created.

You see you already have a C, D and E. That's 3 partitions! If they're all Primary Partitions you must realize that you can only have 4 primary partitions on any drive.

But you should be able to create an extended partition that could hold a lot!

Look at my Gparted snap-shot:

[ATTACH]85150[/ATTACH]

You can see that I have one Windows partition and two Linux OS's with a shared swap. And you can see how much is free in each partition.

---

### Post by kansasnoob on 2008-09-13
Oh, I should have added (referring to my Gparted screenshot), you can see that all of my Linux stuff is in one "extended" partition. So as far as the drive knows I have 2 partitions!

---

### Post by The-Wise-Man on 2008-09-14
Never mind I didn't see page 2.

---

### Post by dudeua on 2008-09-14
I don't believe the problem is caused by fragmented disk or primary/logic partitions.

You can see what Vista shows about my hdd. I deleted that NTFS patition, but no luck - GParted still doesn't see it. 

In my opinion the problem is connected to the hardware configuration of my PC. Perhaps it is the way my hdd and dvd are connected to the motherboard. If the problem would be with partitions, the GParted should at least show me the existing ones, but it shows nothing. It doesn't understand my HDD at all!

---

### Post by dudeua on 2008-09-15
Ok, after A LOT OF searching I finally was able to detect my problem. 
It's described here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502)

and here: 
[http://ubuntuforums.org/showthread.php?t=234706&highlight=jmicron&page=30](http://ubuntuforums.org/showthread.php?t=234706&highlight=jmicron&page=30)

In general, the bug is incompatibility of Ubuntu and jMicron. 

So, can anybody suggest a solution other from updating my BIOS (which I will try later today)?

---

### Post by king james on 2008-09-17
I have found an issue with my MB in that the bios, if set to ide mode, will not detect my disk under linux. AHCI mode will, however. Something to try....

---

### Post by stalkingwolf on 2008-09-17
while booting your GParted Live CD , watch the text.  Does it say that your
HDD, should be HDA* or SDA* is write protected and that it is booting "Read Only"?  I have had this situation and the only solution **I**have found
is to fdisk, repartition the drive and format the drive.

---

