---
title: "Partition Error when performing fresh Ubuntu 14.04.3"
date: 2016-01-06
forum: New to Ubuntu
---

### Post by jimmy46 on 2016-01-06
Recently my laptop began to crash and wouldn't boot up from windows 10 so I decided to do a fresh install of Ubuntu.

I am using a usb to boot into ubuntu

My computer is a HP g6 pavillion. Using disk utility it says hdd is ok but with 200 bad sectors.

When I do a fresh install, I use the setting to wipe everything from my drive but during the process it will keep showing a partition error along the lines of "The attempt to mount a file system with type vfat (partition#1) at /boot/efi failed".

I am trying to figure out if this is a hdd issue or a software issue with the installation process.

---

### Post by bcschmerker on 2016-01-06
**It is in fact an HDD issue.**  Physically out-of-alignment hard-disc assemblies are common for high-gross-operational-hours situations and not rectifiable by the end user.  From all indications the HDD in your Hewlett-Packard® Pavilion G6 is at the end of its service life and will have to be replaced; Seagate®, Western Digital® and Toshiba® all have likely successor models in the 2.5" size format.  Barring backups, unfortunately, extracting remaining files from the known bad sectors is a specialty job for a data-recovery service.

---

### Post by jimmy46 on 2016-01-06
Is that enough indication that the hdd is no longer usable? 

Is there any tests I can do? I used to be able to use the laptop diagnostics for hdd but now it just says the tests arn't installed which does lead me to believe it is a hdd issue.

I am fine with losing all my data just don't want order a hdd and find out it was another issue.

---

### Post by cariboo on 2016-01-07
I'd suggest running from the Live DVD/USB then run  gnome-disks and select Smartdata & self test from the menu. This will show if the disk is failing, or has failed.

---

### Post by Bucky Ball on 2016-01-07
> **cariboo said:**
> I'd suggest running from the Live DVD/USB then run  gnome-disks and select Smartdata & self test from the menu. This will show if the disk is failing, or has failed.

+1. If it doesn't fail, launch Gparted from the live session, delete any partition on there and create a new partition table. You should be able to add whaever partitions you like if you use 'Something else' during install or add them with Gparted in the Live session.

---

### Post by jimmy46 on 2016-01-07
I am assuming gnome disk is just disk in Ubuntu 14.04.

I just did it and it says overall assessment is Disk is OK with 200 bad sectors.

All assessments passed except for Airflow temperature which says failed in the past. 
Is this enough to say that I can't use this hdd anymore?

Also I have tried individual partitions but it still shows the same error.

---

### Post by Bucky Ball on 2016-01-07
Back up while you can and wait for the crash. I would. Bad sectors are unfixable. :|

Also [check this]("http://ubuntuforums.org/showthread.php?t=1970725"). Try a search for 'fix bad sectors ubuntu' and make your decision. I'd back up as soon as possible if you have valuable data on there regardless of what you eventually decide.

---

### Post by jimmy46 on 2016-01-07
I think the crash already happened since when I was on Windows 10 every few seconds it become unresponsive and when I shut it down and restarted, it was stuck on the hp boot screen and never booted up to windows again.

So is it safe to say that a new hdd will solve the issue?

---

### Post by Bucky Ball on 2016-01-07
> **jimmy46 said:**
> 

So is it safe to say that a new hdd will solve the issue?

By the sounds of it, yes. If you are having issues in both Win and Ubuntu and showing 200 bad sectors, that would be hardware.

---

