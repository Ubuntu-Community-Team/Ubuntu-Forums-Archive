---
title: "Installation of Windows Vista after installation of Ubuntu 12.04"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by akira87 on 2013-03-30
Hi,

I need a window platform for my work, so I am trying to install back windows vista back on my laptop after I installed Ubuntu 12.04. Unfortunately, I have accidentally deleted the partition that houses the recovery information for my laptop. May I know what I can to salvage the situation.

Nonetheless, I have a windows XP installation disc with me. I tried to install windows XP after running gParted to partition my HDD into ntfs so that it can be read by the windows installation disc. Although the installation disc is able to run, after loading all the files, the laptop will enter into a blue screen indicating that there is a system fault with the hardware but it is working fine when it is running under ubuntu 12.04.

Thanks a lot.

---

### Post by 73ckn797 on 2013-03-30
You may need to create and format the partition using the XP install disk during the initial steps.

---

### Post by fantab on 2013-03-30
Both Windows XP and Vista need to be installed on the FIRST PARTITION of the booting HDD. Assuming you have only ONE HDD, /dev/sda, then Windows has to be installed on /dev/sda1 only. If I were in your situation, I would REINSTALL UBUNTU after installing Windows.

Also Windows needs its C: partition to have, at least, 25% of free space for it work at optimal performance, AFAIK.

So, my suggestion to you is BACK UP all your important DATA and re-install both Windows and Ubuntu; and in that order. Delete all the partitions with Gparted from Ubuntu LiveCD/USB, BUT Use your Windows Install media to create Windows partitions.

If you have a your Windows Activation Key for VISTA then download the same version of Vista and use your KEY. Or visit your laptop's service centre.

Good Luck...

---

### Post by AndyOpie150 on 2013-03-30
+1 ^

---

### Post by akira87 on 2013-03-30
I have tried to install Windows XP first but the XP cant be installed after it finished loading the files and just display the blue screen of death with the indication that there's a Hard Disk failure etc. May I know how can I resolve this issue so that I can install XP successfully? Thanks.

---

### Post by fantab on 2013-03-30
> **akira87 said:**
> I have tried to install Windows XP first but the XP cant be installed after it finished loading the files and just display the blue screen of death with the indication that there's a Hard Disk failure etc. May I know how can I resolve this issue so that I can install XP successfully? Thanks.

From Ubuntu LiveCD/USB open "DISKS" and run SMART tests on your HDD... see what it says.

---

### Post by akira87 on 2013-03-30
It mention that the disk is healthy.

---

### Post by cmcanulty on 2013-03-30
Go to gparted and format entire disk to ntfs then try XP again. WARNING this erases everything!

---

### Post by Mark Phelps on 2013-03-30
This is a guess, but there could be a problem with hard disk controller drivers if your Win XP disk is an early version, that is, predates SP1.  Ubuntu 12.04 wouldn't have this problem because it's newer and would contain all the SATA Controller drivers needed.

What you might need is the disk controller drivers for the SATA and PATA interfaces on your motherboard. Since your laptop probably didn't come with any disk media, you should Google for it, find the sellers website, and see what they offer in terms of downloads.  There should be motherboard drivers or SATA/PATA drivers there.  IF there are, you need to download those, write them to CD or USB and, when you go to install XP, there will be a screen where you have the option to add drivers.  At that point, insert the CD/USB and let Windows copy in the drivers.

Another approach, which would take longer, is to contact the seller of the laptop, tell them your system go infected and you had to erase the drive, and see what they will do in terms of selling you a set of full-restore CDs.  Using those, you can restore the laptop to factory condition.

---

### Post by mharv on 2013-03-30
There's always some risk in installing/reinstalling OS's or messing with bootloaders/partitions (software, documentation, or user errors can be at fault). Virtualization is a lot safer and simpler unless you have specific hardware requirements.
[https://www.virtualbox.org/](https://www.virtualbox.org/)
Never install Windows AFTER Linux because Windows does not give you the option of not installing their own MBR which will overwrite the Linux one which was allowing dual-boot. 
This links should help: [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

And then this: > there could be a problem with hard disk controller drivers if your Win XP disk is an early version, that is, predates SP1
If this is the case I recommend throwing that CD in the trash immediately .

---

### Post by akira87 on 2013-04-13
Thanks people!! I will try it out again.

---

### Post by Mark Phelps on 2013-04-13
There's most probably no where you can download Vista anymore, not even from MS. Your best bet of getting Vista back is what I suggested weeks ago -- contact the laptop seller, tell them the hard drive got infected with a virus, so you erased is, and the restore isn't working -- and you want to purchase full-restore disk media. Sometimes, they will let you have that for as little as $10.

---

### Post by fantab on 2013-04-13
OP can try torrents websites. Windows Vista is plenty out there. But try to get a copy from a trusted uploader. I you have the product key then you can use it to activate it. But you have to get the exact version of Vista for the key to work.

---

### Post by Mark Phelps on 2013-04-13
> **fantab said:**
> OP can try torrents websites. Windows Vista is plenty out there. But try to get a copy from a trusted uploader. I you have the product key then you can use it to activate it. But you have to get the exact version of Vista for the key to work.

This is all true ... and a torrent version is, of course, free -- as in free beer; unfortunately, it also generally is  not free --  of malware, that is.  It also won't have the drivers for the PC included -- OP will have to hunt for them and download them.

In contrast, the paid-for restore version will come from a trusted source, will be free of malware, and will contain the needed drivers.

Choice depends on what's important.

---

### Post by monkeybrain2012 on 2013-04-13
Can you install Win in virtualbox?

---

### Post by jimafternoon on 2013-04-13
deleted

---

