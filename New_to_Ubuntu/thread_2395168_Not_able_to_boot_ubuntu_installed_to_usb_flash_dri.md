---
title: "Not able to boot ubuntu installed to usb flash drive"
date: 2018-06-27
forum: New to Ubuntu
---

### Post by danx819 on 2018-06-27
Hi! I'm new to linux and ubuntu and I'm trying to install ubuntu to a 64 gigs flash drive following procedures found on youtube. I have a live version of ubuntu on a 8 gigs flash drive and everything works fine. I followed exactly two tutorial that were doing pretty much the same thing: Installing ubuntu with "something else", than make two partitions (one 8 gigs for the swap and the rest for ubuntu (ext4)) I mount at / and I put the boot loader directly on the flash drive and not a partition. Everything looks fine, but when I reboot my computer and I remove the live ubuntu, I can't see the one that I just installed... In both tutorial they were seeing it(when pressed on F12), but I just see windows boot manager. I put the USB first one in the bios and tried on two computers without success, and I see the live one every time... pretty annoying... I run the boot-repair and I received this link: [COLOR=#000000][FONT=Calibri]http://paste.ubuntu.com/p/sJrj6jHj9G/ I tried to find someone else with the same issue, but I found nothing. Could it be just that there's something wrong with the usb key or do I need to add something on the usb to be able to see ubuntu in the boot menu ? Thank you for your time![/FONT][/COLOR]

---

### Post by oldfred on 2018-06-27
It looks like you have an UEFI system with gpt partitioning.
But installed Ubuntu onto flash drive with BIOS boot and MBR(msdos) partitioning.

But have Ubuntu UEFI boot entries in the ESP - efi system partition on sda's ESP. 
That could be a mixed UEFI boot to sdc which is MBR. That normally is not recommended as gpt is UEFI's recommendation.

I have full installs to flash drives booting with BIOS and with UEFI and both use gpt. But I have to partition in advance. With BIOS, you use Something Else and just install grub boot loader to Ubuntu drive (your sdc).
With UEFI, the selection in Something Else of boot loader location is ignored. You have to create in advance an ESP on flash drive, copy /EFI/ubuntu from sda's ESP to flash drive's ESP and then copy again and rename shimx64.efi to bootx64.efi. That is because UEFI only boots external devices from EFI/bootx64 and grub only installs to /EFI/ubuntu (with normal install).

Do you want UEFI boot or BIOS boot? 

Currently not easy to have both. But developer notes in Cosmic are discussing allowing both. I put both an ESP & bios_grub partition on flash drive, but configure for one or the other.

        Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or
sudo parted /dev/sda mklabel gpt 

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[*]/swapfile                                 none            swap    sw              0       0
[/LIST]
     
One of my flash drives:
       ```
Disk /dev/sdc: 61.9GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:  
   Number  Start   End     Size    File system  Name       Flags
 1      1049kB  211MB   210MB   fat32        ESP        boot, esp
 2      211MB   213MB   2097kB               bios_grub
 3      213MB   22.9GB  22.6GB  ext4         system
 4      22.9GB  61.9GB  39.1GB  ext4         data
```

---

### Post by danx819 on 2018-06-28
Thank you for your reply. I must admit thought that I'm a little bit overwhelmed by all this information. I will try to summarize what I understood and please correct me if I'm wrong: I can either boot by UEFI or BIOS (from what I've read, they look pretty similar in terms of uses... ?) and in my case, my problem is that my sda boot is in UEFI but the Ununtu that I installed is in BIOS, so I can't have both. If I want to boot in bios, (I'm not sure what I have to do...) reinstall and make two partition with sdc2, one mounted at /(25-30gig) and the other one mounted /home(the rest -2gig) and 2 gig for swap(if I use ubuntu 18.04 from what you're saying I dont't need this partition ?) and put the boot loader on the flash drive(when you use the boot loader, is it the same thing as flagging it bios_grub ?) and that's it... (now I'm still not sure what my problem was since the only differnce from what I did is to split sdc2...) and if I want to use UEFI boot, I must make in advance a partition(fat32 with boot flag) where I copy the /EFI/Ubuntu from sda to sdc and rename [COLOR=#000000]shimx64.efi to [/COLOR][COLOR=#000000]bootx64.efi and than proceed with install with "something else" and don't use the boot loader (do I need a swap ?). Is that it ? and I'm not sure to understand when I have to do this part: [/COLOR][COLOR=#000000]Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or[/COLOR]
[COLOR=#000000]sudo parted /dev/sda mklabel gpt (and is it really sda ?) Sorry for my ignorance and all my questions and thank you for your help![/COLOR]

---

### Post by oldfred on 2018-06-28
Yes this would be more correct if you want gpt.
sudo parted /dev/sdX mklabel gpt # where sdX is your drive sda, sdb do not run on drive with data you want to keep or it erases it

You need to decide if you want BIOS or UEFI.
BIOS is relatively simple. Partitioning can be either MBR or gpt.
And you just need to install grub to MBR of external drive.

You probably can just use Boot-Repair booted in BIOS/CSM/Legacy mode and using advanced mode, just choose external drive and MBR of external drive for grub boot loader.

One advantage of converting to gpt and having both an ESP and bios_grub means you can do BIOS boot now, but easily convert to UEFI boot latter. If not converted now, you would have to totally reparition later to convert to UEFI. But you may never need that.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
    

All the rest I complicated with the conversion to gpt, which I do prefer if UEFI or even if BIOS.
And if UEFI boot is a bit more complicated to configure for external devices.
I started converting all new drives to gpt with my old BIOS system. And then when Windows 8 used UEFI made both an ESP & bios_grub on every new gpt partitioned drive.

---

### Post by danx819 on 2018-06-28
I tried to do as you told me for BIOS booting (I still added the partition for UEFI if I want to use it in the futur) but I am still not able to boot. I run the boot-repair again and here is the result: [http://paste.ubuntu.com/p/JXmgMP7VjW/](http://paste.ubuntu.com/p/JXmgMP7VjW/) 

1- I noticed that it is written "No boot loader is installed in the MBR of /dev/sdb" but since I used gpt, do I need one... ? And if yes, how can I do that ?

2- I also was not sure about the bios_grub partition (as you can see, I used BIOS boot partition, was it ok ?)

3- And finally I tried to figure out how to "copy /EFI/ubuntu from sda's ESP to flash drive's ESP and then copy again and rename shimx64.efi to bootx64.efi." but I do not know where to find the /EFI/ubuntu and not sure why I have to copy it and then copy it again ? and the problem is also that I cannot access to the sdb files since I am not the owner, so how can I add the copy of /EFI/ubuntu into that ?

---

### Post by oldfred on 2018-06-28
It looks like you copied files as they are in the ESP on sdb.

It looks like Windows is still hibernated, which can cause lots of issues. Note that Windows on updates will turn this back on, so if issues, one of the first things to check.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

It looks like from UEFI in UEFI mode, you should be able to boot from UEFI using ubuntu entry from sda or bootx64.efi from external drive booting external drive directly.
I see Acer, have you enabled trust on the ubuntu entries in sda's ESP. 
And can you use UEFI boot menu and see a separate entry for USB drive?

Since in UEFI boot mode, you technically do not need the bios_grub and will not have any boot loader in the gpt protective MBR. All boot files with UEFI are in the ESP - efi system partition.

But if too many issues getting UEFI to boot, then we can easily use Boot-Repair's advanced mode to uninstall the UEFI version of grub and install the BIOS boot version of grub to sdb. And then bios_grub would be used. And vice-versa.

Currently you can only have either the UEFI grub or the BIOS grub. 
But the developers seem to be discussing allowing both to be installed at same time in 18.10, and then either or both could be installed without uninstalling the other.

---

### Post by danx819 on 2018-06-29
I tried many things and I finally have something working ! I copied the file shimx64.efi from /EFI/ubuntu from the sdb ESP one folder up to /EFI and rename it bootx64.efi. It seems that I didn't need to take the one from sda's ESP. So I guess I will stick with UEFI since it works great. Thank you very much for your help and your time, I learned a lot of stuff and I now have what I was looking for! :) Have a nice day!

---

