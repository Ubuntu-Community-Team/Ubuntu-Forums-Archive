---
title: "Neither gparted or ubiquity allow me to partition my xp on acer 100 notebook"
date: 2014-10-07
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-10-07
I have xp on  an acer 100 notebook. xp won't boot, system registry failure. I attempted to install u14,04 using usb drive as acer has no optical drive. I ran gparted from live dvd. gparted could not find xp end point and would not allow me to shrink xp. I attempted to install u14.04 using ubiquity installer. ubiquity would not allow me to shrink xp. I would like to keep xp. Is there a way for me to shrink xp by 40GB for ubuntu install? Is there a way create a xp usb drive using ubuntu on another computer using xp installation disk?

---

### Post by Vladlenin5000 on 2014-10-07
It's always preferable to use Windows tools to shrink Windows partitions.
Considering yours doesn't boot and you want to keep it anyway, I suggest you first recover that OS which is EoL and no longer supported, something you should be aware of.

---

### Post by grahammechanical on 2014-10-07
The reason why XP will not boot could also be the reason why Gparted and Ubiquity will not partition the hard disk. The hard disk may be failing. There may be something wrong with the partitioning table.

---

### Post by fantab on 2014-10-07
Boot Ubuntu dvd/usb in "Try ubuntu' mode, open Terminal, run the following commands and post its output here:
```
sudo fdisk -l
sudo parted -l
```

You must also use the 'Disks' utility from Ubuntu and run SMART tests on your HDD... the tests will confirm the state of your HDD.

---

### Post by nu2u904 on 2014-10-07
I agree.. I originally shrank xp using xp when I installed u8.04. Unfortunately I only shrank it by 8GB. I had no problem upgrading to u10.04 which is operational. u12.04 is available however  I only have <.5GB. I was able to boot live u13.4 and used gparted to shrink xp an additional 21GB on which I created ext3 filesystem. I saved home to 500GB external drive. I would like to save the whole ubuntu image on the 8GB partition. I would then delete u10.04 and install u14.04 on the 21GB partition.

Since the hp Compaq bios doesn't support bootable usb thumb drives I will have to use the non responding cd/dvd drive.

How can I check the status of my cd/dvd drive? Since that initial booting u13.10 as a live cd/dvd I have not been able to boot any Ubuntu versions.

---

### Post by nu2u904 on 2014-10-07
> **Vladlenin5000 said:**
> It's always preferable to use Windows tools to shrink Windows partitions.
Considering yours doesn't boot and you want to keep it anyway, I suggest you first recover that OS which is EoL and no longer supported, something you should be aware of.

Confused?  My reply was meant for my other thread. I would appreciate your response anyway to that reply.

I didn't use windows as its broke [system error corrupted or missing file register hive]. I now have an xp install disk that I'll upload to my hpZ400 ws running u14.04 and then install  a program to create a bootable thumb drive that I will use to boot xp into the acer100 and be able to enter the 'r' recovery mode and thus repair xp.

---

### Post by nu2u904 on 2014-10-07
I will provide this info as soon as I get home and have access to that computer

---

### Post by Vladlenin5000 on 2014-10-07
> **nu2u904 said:**
> Confused?  My reply was meant for my other thread. I would appreciate your response anyway to that reply.

I didn't use windows as its broke [system error corrupted or missing file register hive]. I now have an xp install disk that I'll upload to my hpZ400 ws running u14.04 and then install  a program to create a bootable thumb drive that I will use to boot xp into the acer100 and be able to enter the 'r' recovery mode and thus repair xp.

Sorry, I don't follow... What has your other thread - AFAICT about a completely different computer - to do with it? My post was directed to your original post in this thread only...
Confused about what exactly?
When I say *it's always preferable to use Windows tools to shrink Windows partitions*, it means that although you can resize NTFS partitions with GParted and other Linux tools, such operation should be carried out from within the Windows system installed in - or using - those partitions, with its own tools, then immediately reboot into Windows to allow *chkdsk *to check and correct eventual logical errors in the resized drive (some recommend doing this TWICE). Then - and only then - proceed to install Ubuntu in the now unallocated space and setup the dual-boot.
 
Now, *considering yours doesn't boot and you want to keep it anyway, I suggest  you first recover that OS which is EoL and no longer supported,  something you should be aware of*.
This is just a friendly reminder: You shouldn't be using XP now for the aforementioned and obvious reasons. However, it seems you want it anyway. Considering that then you better first recover XP up to an usable state and only then perform the resizing as mentioned several times already.

_All of the previous considerations just assume you're working with a known good drive_. ***Important*: **As mentioned in several posts already you should check that drive before anything else. There's no point in working in a failing drive due to old age or whatever...

PS - I strongly recommend you to ditch Windows XP. If you need Windows and the PC supports it, get a Windows 7.

---

