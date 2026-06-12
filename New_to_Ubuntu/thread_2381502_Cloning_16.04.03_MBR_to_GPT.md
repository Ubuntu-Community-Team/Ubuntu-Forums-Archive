---
title: "Cloning 16.04.03 MBR to GPT"
date: 2018-01-01
forum: New to Ubuntu
---

### Post by wokie22 on 2018-01-01
Im trying to migrate a dual boot MBR disk to dual boot GPT disk (its a bigger capacity disk), an attain the new desired setup listed below.  It is a triple boot setup, but only the dual boot MBR disk needs to be copied. 


Setup (Old)


hd1: MBR style w7 OS only


hd2: MBR style W7 data (from hd1)


hd3: MBR style w7 OS+data and Ubuntu


Grub2 on Hd3. Easily select which part I`d want.


////////////////////////


Setup (new desired)


hda1: MBR style w7 OS only 


hda2: MBR style W7 data (from hd1)


hda3: GPT style w7 OS+data and Ubuntu


Grub2 in EFI parition of HD3 to select which part I`d want to boot into.

---

### Post by oldfred on 2018-01-01
You cannot on one drive mix MBR & gpt, a drive is either one or the other.
Windows only boots in BIOS mode from MBR and only in UEFI mode from gpt.
You can keep old drive MBR and have new drive gpt.
And from gpt you can still boot Ubuntu in BIOS mode, if older system but may want the ESP - efi system partition to make it easier to convert drive to UEFI boot without total reconfiguration.

If you want gpt, you have to reinstall Windows 7 in UEFI mode. The DVD is BIOS only, but can be copied to a flash drive and a few files moved around/renamed to make flash drive UEFI bootable.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

You also cannot easily clone partitions to gpt. The gpt configuration has both partition table, backup partition table and each partition with lots more detail and all data in all 3 places must match.

If system is UEFI, better to reinstall all systems in UEFI boot mode, eventually you will want that anyhow.You can copy data like Ubuntu's /home into new install (or separate /home partition).

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by wokie22 on 2018-01-01
Thanks for the response. 

So heres what I understand/have done. 
Key:
HD1 +2 Have W7 OS + and Data respectively installed legacy mode.MBR. This I didnt touch left it alone. 


HD3 refers to old disk formatted with MBR
HDA3 refers to new disk formatted with GPT



In regards to HD3 and HDA3
On the new GPT disk (made sure to use GPart live to convert disk to GPT before anything)
Installed a fresh W7 install (UEFI mode). Install created EFI parition and regular parition
Partcloned w7 off HD3 over the w7 parition (avoid the efi and microsoft reserved). 
HDA3 boots up W7 now fine. 

Now here lies the bulk of my issue. 
How do i get Ubuntu off HD3 and onto HDA3? 

What I have tried thus far?
Partcloned both ext4 parition from HD3 onto HDA3. I can see both paritions, but cannot access it since GRUB2 was not in EFI. (boot repair made no difference). 

Installed a Ubuntu in UEFI mode onto HDA3. Ubuntu booted up fine. Windows also booted up fine. Now the issue is two part. New install is great, but how do i transfer all user data and application data to the new install. Second, how will Grub2 find HD1+2, as running boot repair or grub customizer did nothing to help grub2 to recognize the other w7 install on HD1/2

So then I formatted the new Ubuntu install, clonezillaed back the old install and ran boot repair. It semi worked. Grub2 boots into the old setup on HDA3, however its painstakingly slow. Grub2 W7 entry on HDA3 is broken, however selecting Windows from MB UEFI boot manager is working. 

So basically running down a rabbit hole....

---

### Post by oldfred on 2018-01-01
UEFI & BIOS are not compatible.
So if you have both UEFI installs & BIOS installs, you will only be able to boot from grub installs in same boot mode.
But from UEFI boot menu, you then can choose (some have to turn on/off UEFI/CSM mode) which drive/UEFI to boot.

My backup procedure has the info I need to restore a system. I prefer to do a new install, reinstall apps, copy /home back in & I have most of my data in /mnt/data which is just another ext4 partition with ownership & permissions similar to /home for my use.
I used to have XP, and also then had a shared NTFS data partition for that data I wanted in both installs, like Firefox & Thunderbird profiles & all photos as back then I used Picasa.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834) 

Please post this, so we really know your drive/partitions. Linux uses drives like sda, sdb etc and partitions are the number after like sda1, sda2 etc.

sudo parted -l

You have to be careful cloning partitions. Never to gpt and if you are keeping a clone drive plugged in, you must change UUIDs or you have conflicts.

       sudo blkid -c /dev/null -o list 
and/or:
      
 lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT

---

