---
title: "Newbie to Ubuntu looking for help/advice"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Marcel Beaudoin on 2008-11-07
Due to a fairly catastrophic HD crash, I now find myself in possession of a virgin 250 GB HD. I am taking the plunge and plan on installing Ubuntu on it (am DLing it as we speak), but due to other stuff that I do that runs on the MS .net frameowrk, I also need to have Windows installed.

For whatever reason, my Windows install disk is not bootable, however it appears that the Ubuntu one is.

Is it better to install windows first and then Ubuntu, or the other way 
around?

What are the things that I should keep in mind while installing Ubuntu?

Can I use a common data partition, or do I need one for Ubuntu and one for Windows? By taht I mean, I will have a Windows OS partition, an Ubuntu OS partition, a Windows Data partition and a Ubuntu data partition.

Any help/advice/suggestions would be greatly appreciated.

---

### Post by silverraindog on 2008-11-07
i would install windows first, then ubuntu, windows like to install itself at the beginning of the drive. The way i have my setup is 3 partitions, windows, linux and an ntfs storage one.

---

### Post by dracayr on 2008-11-07
Always install windows first, as windows won't include an already installed linux version in its bootloader. 

What you should keep in mind: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

you can use *one* data partition for both ubuntu and windows.

EDIT: I would use FAT32 for the data partition

dracayr

---

### Post by Marcel Beaudoin on 2008-11-07
> **silverraindog said:**
> i would install windows first, then ubuntu, windows like to install itself at the beginning of the drive. The way i have my setup is 3 partitions, windows, linux and an ntfs storage one.

I was afraid of that. Oh well. I have found some pages that show how to burn a non-bootable windows installation disk image and make it a bootable copy.

> **dracayr said:**
> Always install windows first, as windows won't include an already installed linux version in its bootloader. 

What you should keep in mind: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

you can use *one* data partition for both ubuntu and windows.

EDIT: I would use FAT32 for the data partition

dracayr

Thanks to the both of you for the info!! It is much appreciated.

---

### Post by Coreigh on 2008-11-07
Yes install Windows first. Ubuntu will "play nice" with the MBR (master boot record) where Windows will not. I also agree with the 3 partitions partition a for Windows ~20GB, partition b for Ubuntu also ~20GB, and the remainder of the disk for shared storage. For maximum compatibility you can use a fat32 file system on the storage partition, but that makes having back-up even more important. Ubuntu has come a long way with NTFS support. Can anyone else confirm it is ok or not to use NTFS on the shared partition? Or you can just not share data between the two and split the disk in half, but that has its downside too.

---

### Post by dracayr on 2008-11-07
well NTFS works, but it's ugly... Also, ubuntu won't mount it if it wasn't unmounted correctly by windows (which is the case in a crash, for example, and that's exactly when you *want* to mount it, to back up your data..

IMO the best alternative to FAT32 is installing the EXT3 drivers on windows.

dracayr

---

### Post by Marcel Beaudoin on 2008-11-07
I have seen mentions in other places about using a virtual machine in Ubuntu to run windows.

I have an idea of what a virtual machine is (Sandbox within ubuntu for other programs to play in), but am not sure how easy it would be to set up, nor how convenient it would be to install/use.

---

### Post by Idefix82 on 2008-11-07
You will notice a performance drop, but then again Ubuntu is faster than Windows. 
Do you mind telling us which programs you need to use? For many programs there are equivalent or better Linux alternatives.

---

### Post by Marcel Beaudoin on 2008-11-07
> **Idefix82 said:**
> You will notice a performance drop, but then again Ubuntu is faster than Windows. 
Do you mind telling us which programs you need to use? For many programs there are equivalent or better Linux alternatives.

The primary reasons are a number of programs being put out by Wizards of the Coast that will be running on the .net framework.

Also things like iTunes, Gimp (image editing), Audacity (sound editing), NERO

Thanks for the advice and suggestions!

---

### Post by Idefix82 on 2008-11-07
I don't know what Wizards of the Coast is, so can't advise you there. But the other things you have named have Linux alternatives. In fact, GIMP is much more at home under Linux than under Windows, being open source.

---

### Post by ExxWhyZee on 2008-11-07
I was informed in using Windows to use [http://www.vmware.com/](http://www.vmware.com/) to run Ubuntu under Windows.  As for now, Windows is installing, then I am off to get VMware to see how it works.
:confused:
Will see how it works.  If it works well, or not, I will try to write back on here.

---

### Post by Marcel Beaudoin on 2008-11-10
So I have installed XP on a 30 GB partition, and have another 220GB partition free.

If I understand the psychocat tutorials right, my best bet would be to have Ubuntu install on its own partition next (about 20 GB), have another partition (approx 10 GB) for /home, and then a small swap file partition, with the balance being a common data partition.

How should the data partition be formatted? IIRC, there is a specific format (EXT3) that works really will with Ubuntu, and that Windows can read with the installation of a small untility (FS-drive).  Is it worth doing this?

---

### Post by ugm6hr on 2008-11-10
> **Marcel Beaudoin said:**
> How should the data partition be formatted? IIRC, there is a specific format (EXT3) that works really will with Ubuntu, and that Windows can read with the installation of a small untility (FS-drive).  Is it worth doing this?

If you are going to do this, why not just use /home as a "data" partition for both OS.  Since I only boot XP every 6-12 months, this works perfectly for me, since Ubuntu is set up to use /home to save files already.

A word of warning though: I use 8.04, and fs-driver works great. However, I have read reports that partitions created by 8.10 are not compatible with fs-driver.

---

### Post by Marcel Beaudoin on 2008-11-10
> **ugm6hr said:**
> If you are going to do this, why not just use /home as a "data" partition for both OS.  Since I only boot XP every 6-12 months, this works perfectly for me, since Ubuntu is set up to use /home to save files already.

YOumean something like this:

P1 - Windows XP
P2 - Ubuntu
P3 - Swap
P4 - data (aka/home partition)

[/quote]A word of warning though: I use 8.04, and fs-driver works great. However, I have read reports that partitions created by 8.10 are not compatible with fs-driver.[/QUOTE]

I formatted it from Windows. I don't know if that maks a difference. But, I guess that when I install Ubuntu, that it will re-format the partition itself if I understand things correctly.

---

### Post by JKBurton on 2008-11-10
I use VMware Workstation 6.5 to run Windows XP under Ubuntu 8.10.  I've been very happy with it, but it costs money. It installs easily, and there's a free 30-day trial, though.

The main advantage VMware offers is (some of) your apps/games requiring DirectX 3D acceleration will work. If you don't need that, there are several open source alternatives that are also great, such as Xen and Virtualbox.  There's a huge list at: [http://en.wikipedia.org/wiki/Comparison_of_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_virtual_machines)

---

### Post by ExxWhyZee on 2008-11-10
Vmware 1.0.7, is installing Ubuntu Server 8.04.  I had 2.0 version of vmware.  Though I did see on a youtube video, not to use that, it said stay to the 1.x versions.  I know almost nothing when it comes to server working, but it is installing onto the virtual workstation.  That is the main reason I am putting it onto this, to learn about it.

---

### Post by ugm6hr on 2008-11-11
> **Marcel Beaudoin said:**
> 
P1 - Windows XP
P2 - Ubuntu
P3 - Swap
P4 - data (aka/home partition)
Yes.

My preference is like this though:
P1 - XP
P2 - extended partition
 P5 - /home
 P6 - / Ubuntu
 P7 - linux-swap

Just feels like I am keeping XP & Linux separate with the extended partition.  Additionally, if you create 4 primary partitions, adding additional partitions later is very difficult.
> I formatted it from Windows. I don't know if that maks a difference. But, I guess that when I install Ubuntu, that it will re-format the partition itself if I understand things correctly.
You can use GParted (System->Administration->Partition Editor) on the LiveCD to reformat it.

---

