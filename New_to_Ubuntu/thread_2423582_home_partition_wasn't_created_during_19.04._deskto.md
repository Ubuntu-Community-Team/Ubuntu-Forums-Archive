---
title: "/home partition wasn't created during 19.04. desktop installation?"
date: 2019-07-25
forum: New to Ubuntu
---

### Post by tlzt777 on 2019-07-25
Hello, I'm new to Linux in general. I used Linux Mint for a short time so I know how to create the basic partition table. Or so I thought lol.

I have a 256GB SSD. A few days ago, I was installing ubuntu 19.04. 64-bit. I created partitions with mount points / and /home, as well as a swap partition. When I restarted my pc, I ended up in UEFI and there was an error saying "Couldn't find bootable device". Tried again, still couldn't boot. I inserted the flashdrive again and picked the reinstall option. Everything seemed to work fine. The 4GB swap partition is there. However, today I noticed that I only have 4GB of space available on both / partition and /home partition. I have a 232GB partition mounted at /media/[username]/[UUID]. That was supposed to be the size of /home. When I open it in Files, it says it's empty, but at the same time I apparently have 215.7/227.3 GB available.

findmnt /home returns nothing, by the way.

What happened?

---

### Post by ajgreeny on 2019-07-25
It sounds as if you installed in UEFI mode but did not have the necessary /EFI partition, usually ~200MB fat32, without which a UEFI system will not boot.

To see all the details it will be best to see exactly where you are at present so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	
 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by tlzt777 on 2019-07-25
[http://paste.ubuntu.com/p/4R29DS6K7S/](http://paste.ubuntu.com/p/4R29DS6K7S/) here it is.

---

### Post by oldfred on 2019-07-25
I think all the auto install options only create / (root).

To get it to use /home that you have or have created in advance, you have to use Something Else and choose (change button) which partition is / and which is /home. If you have data in /home DO NOT check the format box.

You also do not need swap as now installer creates a swap file.

You must have originally installed in BIOS boot mode to MBR partitioned drive. You have grub boot loader in MBR and an extended partition. But now have an ESP - efi system partition and the mount of that partition in fstab so install is now UEFI but on old MBR partitioned drive.
How you boot install media, UEFI or BIOS is then how it installs.
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
UEFI highly recommends the newer gpt partitioning. Windows only installs in UEFI boot mode with gpt and maybe Ubuntu should also.

When partitioning in advance, you have to select gpt over default MBR in gparted. If you just do that now it will erase drive. You can use gdisk to convert to gpt, but must have good backup if you have any data you want to save.

       Converting to or from GPT - must have good backups.
[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]http://www.rodsbooks.com/gdisk/mbr2gpt.html
[/URL]
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr) 
    [URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]
[/URL]

---

### Post by tlzt777 on 2019-07-26
Thank you. Since I started using this laptop a few days ago, I simply decided to reinstall ubuntu and create a new partition table, but leave the ESP as it is. I didn't need to format it, right?
I had no problems booting and /home is properly mounted.

UPDATE: I've successfully done the conversion from MBR to GPT using gdisk.

---

