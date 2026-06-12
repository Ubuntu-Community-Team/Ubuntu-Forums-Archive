---
title: "Hard drive not detected by Ubuntu 10.04 LTS"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by E-Tramp on 2012-04-16
Hi, guys, I am back again.  I have been working on building a new computer that I figured to make a dual boot system and install Ubuntu 10.4 LTS on with a Windows program to be decided on later.  I have had a heck of a time trying to get this computer going, starting with hardware problems.  The reason I am here today is because after installing a temporary windows 7 installation and hating the program because of all of the locked files and files I couldn't change the access on, I decided to go ahead and install my Ubuntu installation.  Imagine my shock when I found that the Ubuntu program wouldn't even detect my 3Tb Hitachi hard drive so I could install it on it.  What is up with that and is there anything that can be done to resolve the problem?

I have been working for years to try and get this system setup and running and this is the first time that I had hardware that it wouldn't even detect.  Am I never going to get this going the way I want to?

The hardware I have is good stuff.  ASUS Rampage III Extreme motherboard, with intel 970 i7 processor, and dual ASUS GeForce 560 CU graphics cards and 24 gigs of Patriot G Series RAM Overclocked to 1333 GHz.

I even tried to use Fedora 15 64 bit and it failed to recognize some systems, such as the motherboard chipset. 

I only have two sata hard drives and one is SATA 2 and the Hitachi is SATA three which is what I intended to use to keep my system running at top speeds possible.  All of my old stuff is PATA and not compatible to my new motherboard.  This is suppose to be the system that runs me through the next ten years or so.  But, I am really having trouble getting it initialized and up and running like I expected to do some time ago.

So, is there any fix for my harddrive problem?  I have the latest BIOS installed on the motherboard, ( to get it to recognize the 3T of harddrive space) and even in Windows I find the programming won't let me format a drive from almost 750 GB of the space on the harddrive for some reason, even though the Disk Manager shows the space there.

Any help would be appreciated.  Thanks.  JK

---

### Post by lukeiamyourfather on 2012-04-16
There are multiple SATA controllers on that motherboard according to the specifications.

[http://www.asus.com/Motherboards/Intel_Socket_1366/Rampage_III_Extreme/#specifications](http://www.asus.com/Motherboards/Intel_Socket_1366/Rampage_III_Extreme/#specifications)

> 
[B]Intel® ICH10R controller : 
6 x SATA 3Gb/s port(s), gray
Support Raid 0, 1, 5, 10[/B]
JMicron® JMB363 controller : 
1 x eSATA 3Gb/s port(s), green
1 x SATA 3Gb/s port(s), black
Marvell® PCIe 9128 controller : *2
2 x SATA 6Gb/s port(s), red


Ubuntu might not work with all of those controllers without having to install the drivers manually. The Intel controller should work though. If the drives are connected to one of the other controllers try moving them to the Intel controller.

---

### Post by E-Tramp on 2012-04-17
OK, I will give it a try, and see what it does.  It is going to be a disappointment if the SATA3 ports are the problem though.  I was looking forward to that extra speed.  Let you know how it works.

---

### Post by oldfred on 2012-04-17
With a 3TB drive you have to format it to gpt. Windows will only boot from gpt with UEFI not BIOS. Most new system are UEFI but will work in BIOS mode. You need a new version of Ubuntu to have better UEFI support. gpt just worked in 10.04 with BIOS, but I had issues chainbooting to Windows in a MBR drive.

Ubuntu/grub will install and boot from gpt with either UEFI or BIOS. But you have to format in advance with the efi partition and install partitions to have a chance of getting it to work and need to boot in UEFI mode for CD or USB. Some install in BIOS and convert  but with gpt & BIOS you need a bios_grub partition which cannot be the efi partition.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)


In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!


Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)

---

### Post by E-Tramp on 2012-04-17
While I am sure you know what you are saying, I think that that is way too much information for a beginner to absorb and figure out.  I will say that I did swap the SATA3 hub for a SATA2 hub, and it found the drive then. So it is the program not seeing the SATA3 hubs as opposed to the drive. Then when I tried to send the installation into the unformatted section at the end of the drive since windows couldn't use it any way, the program told me that, "starting sector number, 4294969344 exceeds the msdos-partition-table-imposed maximum of 4294967295".  If I could install it there it would be ideal, as I can't format that section in Windows anyway.Then it tells me the following when I hit the OK button,"This probably happened because there are too many (primary) partitions in the partition table." 

When I go to "specify the partitions Manually" on the next screen it gives me the opportunity to install the program in any of the partitions then if I select the free space it tells me that "no Root File System is defined" and "please correct this from the partitioning menu".

Unfortunately it doesn't seem like the disk wants to partition the section because it gives me the same error message as above,"starting sector number, 4294969344 exceeds the msdos-partition-table-imposed maximum of 4294967295".  I really am curious as to what MSDOS has to do with Ubuntu. I need some help figuring out what most of this means.  What should be my next move?

---

### Post by lukeiamyourfather on 2012-04-17
> **E-Tramp said:**
> While I am sure you know what you are saying, I think that that is way too much information for a beginner to absorb and figure out.  I will say that I did swap the SATA3 hub for a SATA2 hub, and it found the drive then. So it is the program not seeing the SATA3 hubs as opposed to the drive. Then when I tried to send the installation into the unformatted section at the end of the drive since windows couldn't use it any way, the program told me that, "starting sector number, 4294969344 exceeds the msdos-partition-table-imposed maximum of 4294967295".  If I could install it there it would be ideal, as I can't format that section in Windows anyway.Then it tells me the following when I hit the OK button,"This probably happened because there are too many (primary) partitions in the partition table." 

When I go to "specify the partitions Manually" on the next screen it gives me the opportunity to install the program in any of the partitions then if I select the free space it tells me that "no Root File System is defined" and "please correct this from the partitioning menu".

Unfortunately it doesn't seem like the disk wants to partition the section because it gives me the same error message as above,"starting sector number, 4294969344 exceeds the msdos-partition-table-imposed maximum of 4294967295".  I really am curious as to what MSDOS has to do with Ubuntu. I need some help figuring out what most of this means.  What should be my next move?

What oldfred described in a previous post is what you're talking about. Drives over 2TB need to be handled differently.

---

### Post by oldfred on 2012-04-17
MBR - master boot record and msdos are the partitioning used by computers since the first PC hard drive. It only allows 4 primary partitions since changed to allow one primary to be converted to an extended to hold many logicals. Windows only boots from primary partitions. But back in the 80's the size the set as the maximum it could use was 2TB or 2.2TiB. This was when a large hard drive was in MB not even GB.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

So if your computer has UEFI, you need Windows 7 (I think 64 bit) and install in UEFI mode. Some have reported that installing Windows in UEFI mode still works better than Ubuntu/grub. If you only install Windows in MBR(msdos) mode you only have a 2.2TiB drive and the rest will never be usable.

In all cases it is better to format in advance to gpt. You can use gparted or gdisk.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by E-Tramp on 2012-04-18
OK, This is going to be very difficult.  It is going to take me a while.  I had no idea that this 3TB drive was going to cause me so much work.  So, will be some time looking at all of this and figuring it out.  I am sure that I will have tons of questions, after I have had time to go over all of this.

Here is another question.  I noted in WindowsXP that you could only create 4 partitions and I am not sure if you can include the extended partition as well, but, I know at least four simple could be created, a long time ago, which you obviously mentioned, however, with Winodws 7 I have found that isn't true any longer you can only create 3 simple partitions and one extended partition. If however the drive is partitioned in four simple partitions in WindowsXP Windows7 will see all four, it just won't create four.  Is it just me, or is that a downgrade?  Shouldn't they be increasing the number of partitions and not decreasing them?

I will get back to you as soon as I have had time to study this and figure it out.  I am kind of slow so, be patient with me, us old country boys have think a long time to get all of this.

---

### Post by E-Tramp on 2012-04-18
OK, another question.

Under windows7 there is Legacy support for the old XP programs, and since literally all of my programing is from my XP system, I would like to maintain that support so I can continue to use some or perhaps all of the old programming from my last computer, however:

Note: Windows does not support booting of GPT initialized volumes with UEFI systems on 32-bit versions of Windows, and that that legacy BIOS systems do not support booting of GPT partitioned volumes. Consult with your system vendor to determine if the system supports UEFI and booting of devices greater than 2TB.

Does this mean that if I do partition using GPT that none of the Legacy programming will work even if windows7 supports the old legacy stuff?

---

### Post by oldfred on 2012-04-18
I do not think XP reads gpt at all. But, you can boot from BIOS with Windows 7 on one drive and read the partitions on a gpt NTFS partition.

Otherwise you have to have a newer motherboard with UEFI and the 64bit Windows 7 (or Vista 64bit I think) to boot with gpt.

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

I had/have XP on my older 160GB drive in MBR and dual booted with Ubuntu on a gpt drive since 10.04. But never used XP to read any data from gpt drives. Now I have converted BIOS to AHCI (for SSD) which also does not work with XP, so I rarely boot XP as I have to reset BIOS and not use my new SSD.

Ubuntu boots from gpt whether BIOS or UEFI and dual boots with Windows without issues in most cases.

---

### Post by JKyleOKC on 2012-04-18
> **E-Tramp said:**
> OK, another question.

Under windows7 there is Legacy support for the old XP programs, and since literally all of my programing is from my XP system, I would like to maintain that support so I can continue to use some or perhaps all of the old programming from my last computer, however:

Note: Windows does not support booting of GPT initialized volumes with UEFI systems on 32-bit versions of Windows, and that that legacy BIOS systems do not support booting of GPT partitioned volumes. Consult with your system vendor to determine if the system supports UEFI and booting of devices greater than 2TB.

Does this mean that if I do partition using GPT that none of the Legacy programming will work even if windows7 supports the old legacy stuff?There's another solution that may work for you, once you are able to get the 3-TB drive partitioned and Ubuntu installed and running (without being concerned at this point about running XP). Your hardware specs are much more than good enough to let you install virtualization software and run XP through it. That would mean that you could create a virtual 32-bit machine inside VirtualBox, for instance, and give it a few hundred gigabytes of storage and three or four GB of RAM (although 32-bit XP won't see more than three and a fraction GB of RAM no matter how much you have).

With the hardware you have, there should be no detectable drop-off in performance of the Ubuntu side of things, and the XP virtual machine should perform at least as fast as, and probably faster than, it does on your current XP system.

An additional advantage of this approach is that you would not have to re-boot to switch between Linux and Windows, and could directly communicate between the two systems.

I'm using exactly this approach, with much less capable hardware, to support my Windows customers and to do software development with Delphi 5. It works quite well even with my 3 GB of RAM and 500 GB disk limits, on a dual-core 2.5 GHz CPU...

---

### Post by E-Tramp on 2012-04-20
Well, now that you guys mention it, the V-machine idea has some real appeal, and I could as you say run things simultaneously with either a windows 7 program or an Ubuntu program.  I might just do that and if I do I would come here to get pointed in the right direction on figuring out all of the details.

Thanks for all of the information, guys, and I really have a lot of reading to do now that you have given it too me, so I guess you will understand if I tell you I will be a bit before I come back to ask some more questions.  Tomorrow I have surgery and will be laid up for a while so it will be a good time to read the stuff though that too is a distraction that will make it that much longer till I get it done, U no? Physical therapy and such to recover with.

I will get back to you all as soon as I can though, so, be patient with me.  Be back soon.

---

### Post by JKyleOKC on 2012-04-20
Been there, done that, got the 21-cm plate in my left leg to prove it. Good luck with the surgery and the rehab!

When you're ready, most of us will be here to answer your questions and/or give advice. Till then, work hard at the recovery...

---

### Post by E-Tramp on 2012-05-16
Alright, Guys, I have been studying this stuff for a while now, and was surprised to find that ASUS Rampage III Extreme motherboards don't support UEFI Boot systems. To Old Fred, can I format the 3TB hard drive in GPT, and Boot the system from an SDD?  Will the OS see the Hard drive formatted that way as long as the boot device isn't GPT?

Also, since it appears that the 10.4 doesn't detect my Marvel drive hubs at all due to lack of Drivers for them, can anything be done to correct that? Does 11.4 or 12.4 either one have drivers for Marvel 6GB/s drive hubs?

I would like to get full use of the 3TB hard drive if possible, and yet not able to boot UEFI.  Options anyone?

---

### Post by oldfred on 2012-05-16
Some of the newer hardware is only supported in the new versions of Ubuntu and often the very newest is not supported immediately as they have to reverse engineer most things.

I boot two drives as gpt and two as MBR. My old XP will not read gpt NTFS partitions but I understand Windows 7 will. 

Ubuntu works with gpt whether BIOS or UEFI, it just is that you have to have the extra partitions. With UEFI you have to have the first partition as the efi partition and with BIOS you need  a bios_grub partition. For my new SSD and hope for a new UEFI system soon, I put both partitions on it since repartitioning is difficult when you want to add a first partition. But I boot with BIOS now.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

If you are booting Windows from a MBR SSD, then it should see the gpt drive fine. Ubuntu will either way. 

Have not tried virtual memory install.

---

### Post by E-Tramp on 2012-05-30
OK, I am back again, I have a couple of questions.  The first is I have used The Disk Utility to partition the 3TB HDD, and it is telling me that the partition is misaligned 3072 bytes, and that I should repartition it.  The problem is, if I repartition it it just keeps placing the partition in the same place and the error repeats itself with every partition effort I make.

Any idea's on how to eliminate the alignment error on the harddrive?  I don't seem to be able to come up with a solution for it.

Also, I have divided the SSD into two partitions of 128GB each one for Windows 7 and one for Whatever version of ubuntu I happen to decide to use.  If I go ahead with the Virtual XP environment will I need any additional space on the SDD for the Virtual operating system?  I have never set one of those up before so will be working from scratch.

---

### Post by oldfred on 2012-05-30
I have always used gparted and have had good luck with it. There were some issues with Disk Utility and some newer features, so I do not suggest it except to review partitions or add labels.

What partition is misaligned? Is this the 3TB drive and are you using gpt? I would use gdisk or gparted only.

If the extended in MBR it does not matter as you do not write the extended directly, but all primary & logicals should have start sectors divisible by 8.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by E-Tramp on 2012-06-01
OK, in answer to your question, yes it is the 3TB hard drive that the alignment exists.  I wasn't aware that there was any rules as to where partitions start and stop.  I guess all of that huge space created some strange work arounds that have to be accounted for now.

I will get back to you as soon as I have read these threads and such and you may have to help me figure out what to do to get the alignment where it has to be.  I may have some questions about partitions after I read through this stuff.

---

### Post by zSeries on 2012-06-01
Gparted in the standard repository is out-of-date. You need to download the latest ISO and burn a CD. I used gparted-live-0.12.1-1. There is a new tick box for the MB allignment.

---

### Post by oldfred on 2012-06-01
If installing a new system, use the tools from the new liveCD, not the old one.

I am like zSeries in I often download the newest gparted or parted magic ISO. I directly boot (grub loopmount)  ISO from either anther drive or Flash drive so it is easy to update and not have to burn another CD. I used to use a lot of CDs before a new install as I wanted several ways to boot/repair/install before I started.

I think the last few versions of Ubuntu and all the new gparted tools use 1MB rounding now for better compatibility with SSD & 4K drives. You now may see small bits of unallocated in partition tables. You used to have some unallocated  before but it was smaller and rounded down to not show. Now it is just a bit larger and now shown.

[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by E-Tramp on 2012-06-05
I have some questions now that I have read these links.  I think I pretty much understand the partition alignment now, and the reason for it.  But in order to get a step closer to deciding how to set my drives up I need some additional information.  I have in mind the objective of doing a dual boot system using Windows 7 and Ubuntu 11.4 or 12.4 LTS with a virtual XP program, that I can use with both if possible.

One of my questions is, how should I have my drives partitioned.  I figured on possibly installing both on the SDD which is 256 GB, and have the Virtual XP also on that drive if possible.  The 3TB Hard drive is currently divided into 4 primary partitions and I couldn't get Gparted to allow me to create any other type of partition.  The extended and logical drive choices are blacked out for some reason.

Anyway, am I going to need more than two partitions for the dual boot system on the SDD if I want to Virtualize a Windows XP installation with them, and What would be the best format system for both Windows and Ubuntu.  I see where Ubuntu doesn't like the ntfs format so does that mean I should use FAT32 for both, or do it with different formats for each OS?

---

### Post by oldfred on 2012-06-05
On all MBR(msdos) drives you can only have 4 primary partitions. But you can use only one of the four as an extended partition that can hold many logical partitions.

For very large drives, you do not use MBR, but use gpt. Windows will only install to gpt partitoned drives if booting with UEFI, but Ubuntu will boot gpt drives from BIOS if you add a small 1MB bios_grub flagged partition. (That is what I do.). XP will not read gpt drives, but Windows 7 will if booting from a MBR drive.

Do not use FAT. Both Windows & Linux read NTFS partitions just fine. But Ubuntu has to install to Linux formated partitions to support ownership & permissions that Windows formats do not support.

If you have MBR on your 3TB drive it will only show 2TB. If gpt, gparted should let you create up to 128 partitions.

I do not know anything about virtual installs. I thought Windows 7 had a mode that emulated XP.

---

### Post by E-Tramp on 2012-06-09
I don't believe this, twice now I had this reply going and it deleted because I hit the back space button with the cursor some where it shouldn't be because this laptop is such a piece of crap.

For the third time, yes from what I understand Windows 7 does emulate Windows XP and will run most of the legacy programming from the old XP system however the purpose of creating a virtual environment of Windows XP is to have acess to Windows XP programs from both Windows 7, and Ubuntu 11.4 LTS without having the redundancy of dual installations of programming thus ending up with an overly large system that will be slower because of its duality.  I was hoping that Jim Kyle could tell me some things about VE systems that would make it clear whether it would be possible to access the virtual environment program from both operation systems.  Seems Like it should be possible, if you set it up right.

As for the 3TB harddrive it is formatted with GPT, and I know that Windows XP won't detect it set up that way but, that shouldn't matter because I am hoping that I can set the OS's up on the SDD, Which is 256GB, and I currently have it divided into two partitions, though I know that isn't going to be enough to create the system I have planned.  I do want to do the install  manually, but, I will need some help on the partitioning.

I see several choices of formatting for the partitions, and have no idea which I should use for what.  I haven't downloaded the Gparted program recommended, and am not sure how I would use it while I am using a live disk in the computer to run things at present.  I do have a DVD burner and a Blue Ray burner so I guess I could run two different disks.

There is so much I don't know.

The 3TB drive will just have to be file storage for now I guess.  I wasn't aware of the problems it would be to use it at the time I bought it because I wasn't aware of all of the changes that things had gone through over the last few years.  I am having to learn so much to finish this build, and I am getting frustrated with how things have changed.

Anyway, I guess we could call this thread good, now, and move on to a new thread to get to the installation problems.  Lets finish up with the partitions I will need and if Jim Kyle is around maybe he can give me an idea of the possibility of accessing the VE from both systems.

---

### Post by oldfred on 2012-06-09
I like to have an Ubuntu install on every drive. So even if you primarily boot from the SSD, I might still put an install on the 3TB drive in a smaller partition just to make the drive bootable. Before my SSD, I would rotate my newest install from hard drive to hard drive, so every drive could boot something.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by JKyleOKC on 2012-06-09
I've been quiet for a while but am back now. Unfortunately I don't think what you want to do is possible, since the virtual machine actually resides as a file on the disk drive of its host system, and its virtual disk is another file on the host's drive. It definitely would not be very simple to do...

You might be able to put them on a shared partition and then install VirtualBox in both the Win7 and Ubuntu hosts, but I suspect there will be enough detail differences between the Windows and Linux versions of VBox to keep it from working.

In addition, the differences in permission rules between Windows and Linux may bite you. Since Windows cannot reliably access the Linux file systems, a shared partition almost has to be formatted as NTFS -- and that might not be compatible with VBox.

However, given all these possibilities for failure, it would definitely be worth a try. I wouldn't entrust any production work to it until it had proved its reliability, though...

---

### Post by E-Tramp on 2012-06-26
OK, you guys have been a lot of help.  I now have a good idea of what I can do and what I probably can't.

Jim, is there a thread that explains how to use The VBox programming? Also guys, is there a thread that details the setup on the partitions for 11.4 LTS installation?  I have yet to see what kind of partitions I need for this and this would be using BIOS only.  No UEFI on my motherboard.

Basically, what I think I need is number of partitions, size of partitions, and designation of partitions for the installation disk to work without errors, and finally type of file system for each partition.

Now if you please can you link me to some threads on installation of 11.4LTS? I will then check this thread over and finish it up and post any new questions on another thread spacifically for that question.

---

### Post by JKyleOKC on 2012-06-26
I don't know of any thread that provides the information you're looking for, but when you install VBox it will put a help file that's a very detailed user manual -- better by far than any other manuals I've seen in the past few years -- on your host system, with a menu option to access it. This manual includes full information about all the command-line interfaces to VBox, which are quite a bit more powerful than the GUI interface...

If you need even more help, try [http://forums.virtualbox.org/](http://forums.virtualbox.org/) for the VBox forums, which I've found to be good but nowhere near as responsive as the forums here (however I've not found any other forums that match these for responsiveness).

You must have had a typo referencing 11.04 LTS. The last LTS before 12.04 was 10.04; they only happen in even-numbered years. My partitioning here, for 10.04, on a 500-GB drive, gives 50 GB to "/", 5 GB to swap, and the rest to "/home" (which is where all of my VM files reside). I would expect the same to work for 12.04 equally well. The type is "ext4" for both / and /home; swap doesn't take a type parameter since it's simply a binary dump of RAM pages and has no directory structure.

---

### Post by safir on 2012-06-28
I am also a beginnerto Ubuntu operating system. I installed Ubuntu 12.04 on my computer that has two HDD. Bios shows the presence of both HDDs on the computer but I can't see either one in the file system or under the computer listing. One of the HDD is 500 Gb while the other is 2Tb. When I right click on the Computer or Desktop under the home folder it tells me that volume is unknown and gives me the free space available on the drive. Looking to the amount of free space, I concluded that it is the 500 Gb HDD. But no information about the 2Tb HDD. How can I make operating system show the presence of both drives. I would like to use the 2TB HDD as a storage drive for pictures and music etc. I tried to run gconf-editor in the ALT+F2 dialogue to open the app. But it does not run and gives nothing. Any help will be highly appreciated. Thanks.

---

### Post by E-Tramp on 2012-06-30
So the swap has no format at all?  Bummer on that 11.04.  I really don't like the lack of menus on 12.04.  Guess I might go back to 10.04 or on to 11.10 since it isn't LTS anyway, rather than 12.04.  If they rework the interface in 12 two years from now and put the menus back in, I will see what it looks like then. That search function is just plain awkward for the daily fuctions.

As for Safir,  I don't know enough to answer your question but, I can tell you you should start a thread for your problem and and include a lot more information like hardware you are using.  My problem there turned out to be the Marvell interface and the 3TB hard drive just not liking each other.  The SDD shows up on the Marvell SATA interface just fine.  I don't think you have enough information here for them to help you, and they sort of frown on you jacking other guys threads.  Good luck though, I am sure you will find the answer.

---

### Post by E-Tramp on 2012-06-30
Oh, by the way Jim, the partitions go in the order you stated above on the hard drive, for the sake of the system ease of recognition?

---

### Post by JKyleOKC on 2012-06-30
Actually they go 50, 495, 5 with "swap" being the final one. I just let the installation programs handle the partitioning. All three are primaries and I still have one slot left over to do an extended, should I ever decide to trim "home" back and add additional partitions (which isn't very likely).

As for 12.04, give Xubuntu 12.04 a try before you give up completely on the Pangolin versions. The XFCE manager did NOT go to the Unity interface. I've installed Xubuntu 12.04 on a VM here to check it out, and once the bugs have all worked out of it will probably do an upgrade in place (too many virtual drives to make a backup and clean install practical for me). While the 12.04 has a bit more eye candy than did my Xubuntu 10.04, it's still the same basic look and feel...

---

### Post by E-Tramp on 2012-06-30
OK, Jim I will try that, sounds good, in the mean time I did end up installing the 11.04 on my hard drive without manual interaction at all.  Fortunately it installed in the part of the Hard drive I wanted it to, an unformatted area adjacent to the Windows 7 installation, but, with complications.

First I got an error message that some of the software installation programming was "broken".  Libre Office seemed to be the program that was the victim of the break for the most part.  So, probably would not be installed.  Also, the installation formatted the space as an extended partition, and two partitions of 102 GB ext4, and 26 GB Swap space.  There doesn't seem to be another partition of 50 GB for the "/" partition.  Not only that the Grub appearantly didn't install and won't boot into the program I just installed.

---

### Post by oldfred on 2012-06-30
The auto installer finds and installs to unallocated space. It creates just / (root) & swap and often creates the extended and logical partitions. The install should be ok, once fixed or you can reinstall.

If install did not complete then it did not install the grub2 boot loader correctly. You can usually repair that with this, if the rest of the install is ok. You can run it from your liveCD or USB or download a fully bootable ISO as a repairCD/USB.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by E-Tramp on 2012-07-02
OK, I will study this and figure out how to use it, and see what it will do.  Or, maybe I will just download and burn a disk of Xubuntu 12.4LTS and see if I have better luck with it.  It may be that my live disk got damaged or the original image was corrupted that I downloaded which resulted in the problem.  I don't know if the installation completed, because when the error from the installation came up, it gave the option of trying the installation of the "broken" elements again, and when I selected it the error window closed and nothing else happened so I guess looking back that the installation was unable to finish.  I don't know at what point the Grub is installed but, if the OS wasn't completely installed it might be a waste of time to install the grub if the installation isn't even functional.

Probably be best to just try a different installation and reinstall from scratch.  Won't take a minute to delete the partitions and start over.  Maybe then I can create my own partitions.  So, from what you said I really don't need the extended partition at all, though the installer did use it?

The last time I installed a Linux program the installer gave you a choice of an auto install and a manual install.  Things have obviously changed since then because the installer on 11.04 had no manual option, and that had me sweating during the install because I couldn't see where the installer was putting it.

The last time that happened I had to reinstall my Windows program and my backup drive because Ubuntu installed itself between them instead of where I wanted it in a partition to the right of the backup drive.  Made a lot of work for me and made me gun shy of blind auto installs like that.

If I create the right partitions in the right order will the auto installer put everything where I have it set to go?  Also my swap file was 26GB, and that is quite a bit larger than what you suggested.  In windows the Swap file is suppose to be as big or bigger as the amount of RAM you have.  Since I have 24GB of RAM, do you think that that is why the swap file came out so big?

---

### Post by oldfred on 2012-07-02
Manual install is now called Something Else.

If you partition in advance, you have to use Something Else or you can now create partitions as part of Something else. Either way with Something Else (could not they have just kept Manual?) you have to choose which partition is / (root) and what format ext4, which is /home and its format (but if reusing an old /home  with data, you do not reformat, and if swap already exists it finds it.

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

