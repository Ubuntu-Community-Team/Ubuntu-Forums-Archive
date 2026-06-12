---
title: "Simple dual boot (windows 7/Ubuntu 12.04) with shared data drive"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by mark129 on 2014-04-22
Hello everyone,
I am an inexperienced Ubuntu user with a a new desktop computer with 2 HDD that has Windows 7 Prof. (64 bit) preinstalled. I would like to setup a simple dual boot with Ubuntu 12.04 on the smaller C drive, and use the D drive for data.

System details:
Dell Precision T3610
Intel Xeon CPU E5-1620 v2 @ 3.7 GHz 3.7 GHz
16 GB RAM
HDD C: NTFS 500GB
HDD D: NTFS 2TB

I just wanted to check whether I am likely to run into any problems using the D drive as a shared data area for both OS - is there any risk of corrupting files/directories by accessing files from one OS to the other?

The reason I ask is because I have a similar dual boot on my laptop (that someone else set up for me), but here I just have a single drive partitioned with an area for Windows and one for Ubuntu. The Windows drive is then mounted in Ubuntu so that I can access these files from either OS. I've noticed that accessing files in this way seems to sometimes lead to corruption of files/entire directories. After reading around, this seems to be due to the partitions being formatted completely differently, and is a terrible way to work  - hence why I want to set up the desktop the 'right' way (and if I can figure it out, reconfigure the laptop to use a shared area!) :)

So once I partition the C drive to have an area for each OS, do I need to do anything else with the D drive to make sure it is compatable with both OS, or should it already be fine with the current NTFS formatting?

Also, I get the impression that 500GB is unnecessarily large for just the OS, and maybe at most, I would need ~80GB for windows, and ~20 GB for Ubuntu, and can use the rest of the C drive for something else. Looking at this thread:[http://ubuntuforums.org/showthread.php?t=2214786&highlight=dual+boot+shared+data,]("http://ubuntuforums.org/showthread.php?t=2214786&highlight=dual+boot+shared+data") I can't figure out if it is worth having extra partitions such as '/swap' to store data when the computer hibernates, and in this case, how large should it be? the same size as the RAM?

Many thanks for your help in advance!

---

### Post by sandyd on 2014-04-22
> **mark129 said:**
> Hello everyone,
I am an inexperienced Ubuntu user with a a new desktop computer with 2 HDD that has Windows 7 Prof. (64 bit) preinstalled. I would like to setup a simple dual boot with Ubuntu 12.04 on the smaller C drive, and use the D drive for data.

System details:
Dell Precision T3610
Intel Xeon CPU E5-1620 v2 @ 3.7 GHz 3.7 GHz
16 GB RAM
HDD C: NTFS 500GB
HDD D: NTFS 2TB

I just wanted to check whether I am likely to run into any problems using the D drive as a shared data area for both OS - is there any risk of corrupting files/directories by accessing files from one OS to the other?

The reason I ask is because I have a similar dual boot on my laptop (that someone else set up for me), but here I just have a single drive partitioned with an area for Windows and one for Ubuntu. The Windows drive is then mounted in Ubuntu so that I can access these files from either OS. I've noticed that accessing files in this way seems to sometimes lead to corruption of files/entire directories. After reading around, this seems to be due to the partitions being formatted completely differently, and is a terrible way to work  - hence why I want to set up the desktop the 'right' way (and if I can figure it out, reconfigure the laptop to use a shared area!) :)

So once I partition the C drive to have an area for each OS, do I need to do anything else with the D drive to make sure it is compatable with both OS, or should it already be fine with the current NTFS formatting?

Also, I get the impression that 500GB is unnecessarily large for just the OS, and maybe at most, I would need ~80GB for windows, and ~20 GB for Ubuntu, and can use the rest of the C drive for something else. Looking at this thread:[http://ubuntuforums.org/showthread.php?t=2214786&highlight=dual+boot+shared+data,]("http://ubuntuforums.org/showthread.php?t=2214786&highlight=dual+boot+shared+data") I can't figure out if it is worth having extra partitions such as '/swap' to store data when the computer hibernates, and in this case, how large should it be? the same size as the RAM?

Many thanks for your help in advance!

If you are using windows 8 - you will have to turn off fast boot otherwise there will be corruption of data.

As for the D drive - Ubuntu should be able to read/write to NTFS partitions without issues.

If you want to hibernate, the swap space will have to be larger or equal to the size of the ram on your computer.

---

### Post by oldfred on 2014-04-22
I think hibernation of either Windows or Ubuntu or the Windows 8 always on hibernation or fast boot is the main cause of data corruption. When hibernated the system restores to where is was before, but if you modified it from another install then the modifications will be lost.

Generally best not to hibernate. And set Windows main install partition or c: "drive" as read only. And use the data partition as read/write.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

I do prefer with two drives to have each install on separate drives with its boot loader on the same drive as the install. Then when (not if) one drive fails you can in BIOS or one time boot key boot the other install. But backups and repairCDs or flash drives for the current version of every install are still vital.

---

### Post by mark129 on 2014-04-25
Great, thanks for the advice - I have everything up and running successfully now

---

