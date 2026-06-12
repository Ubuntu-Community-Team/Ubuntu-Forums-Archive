---
title: "No Operating System Found after installing Ubuntu 13.04 to USB on Windows 8 computer"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by LC2013 on 2013-05-30
I'm brand new to Linux and I thought I had figured out what I was supposed to do to install Ubuntu 13.04 to run on my 32 GB USB drive.  I'm positive that when I installed it I had set it to install to the flash drive (it was listed as dev/sdc, with 32 GB, in the installation type menu), so I had thought that this would not affect my current operating system, Windows 8. But after the installation was complete and I restarted my computer I got the same menu from before asking if wanted to install ubuntu or try it without installing. If I turn on the computer without the flash drive in I simply get a black screen with the message No Operating System Found. I had a Windows 8 operating system before, has it been messed up or removed? Or does it have something to do with the way the computer is booting? I knew how to change the boot priority under Windows 8, but I don't know how to do the equivalent in Linux. I'm sorry if I sound completely uninformed this really is a lot more complicated to me than I'd thought it would be. Please help!!!!

---

### Post by mastablasta on 2013-05-31
> **LC2013 said:**
>  But after the installation was complete and I restarted my computer I got the same menu from before asking if wanted to install ubuntu or try it without installing. If I turn on the computer without the flash drive in I simply get a black screen with the message No Operating System Found. I had a Windows 8 operating system before, has it been messed up or removed?

assuming you really installed it propperly (which i don't think it's the case - did you format the USB? if so hwocome you can still perform liveboot? from where did you install it to USB?):

you installed grub on your hard disk. you should have chose (using manual partition) to install it on USB. 

solution - boot with windows repair disk and restore the master boot record. this will solve the windows issue. [http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/](http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/)

now install GRUB (which is linux version of MBR) on USB disk.[http://askubuntu.com/questions/10571/how-to-install-grub-on-usb-flash-drive](http://askubuntu.com/questions/10571/how-to-install-grub-on-usb-flash-drive)

though in your case i would reinstall the whole hting since i doubt you did it propperly. if oyu think oyu did install it propperly then use this tool to create bootinfo summar and post it here int he forums: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

do you maybe have UEFI?&#382;

additional info regarding install on USB: [http://ubuntuforums.org/showthread.php?t=2088113](http://ubuntuforums.org/showthread.php?t=2088113)

---

### Post by cub on 2013-05-31
Just to check, did you change any boot order in BIOS before booting to he USB the first time? If so, could it be that boot is set to only boot from USB?

---

### Post by LC2013 on 2013-05-31
I did change the BIOS order before booting to the USB and I know that before I installed I could boot to both the hard drive and the USB just fine.

Thank you, I will try rebooting with the windows repair disc.

As far as formatting my USB, I chose "Something else" for installation type and set up the root, home, and swap partitions under dev/sdc in the installation type menu, which I had assumed was my flash drive because it showed 32 GB of free space and also the only other device shown was dev/sda which contained used space so I assumed that that was my hard drive. Perhaps I misunderstood this part of the installation process.

 Evidently it did install Ubuntu to my USB because if I start the install again it says Ubuntu 13.04 is already there. When I choose "Something else" this time I find the same partitions I set up on my USB from before but this time only one device, so I can't find my hard drive.

Thank you for the replies. At this point I would be happy to get Windows running again. If that happens I may try with more caution and help to reinstall Ubuntu 13.04 to the flash drive.

---

### Post by presence1960 on 2013-05-31
Boot the USB and don't choose to install. When the desktop loads open a terminal and run ```
sudo fdisk -l
```
That is a lowercase L at the end of that command. This will show your partition table. Post the output back here.

---

### Post by LC2013 on 2013-05-31
> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x53128d6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e33f40d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1    62533295    31266647+  ee  GPT

Disk /dev/sdb: 32.2 GB, 32176472064 bytes
256 heads, 30 sectors/track, 8182 cylinders, total 62844672 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          96    62844671    31422288    c  W95 FAT32 (LBA)
 

Okay, there's what I got.

---

### Post by mastablasta on 2013-05-31
ok so you did it correctly but you missed one step. the GRUB should have been put to USB disk and this needs to be done manually. i mean default setting is to put it on hard disk which is normal if one would want to install the OS to hard disk. so oyu put that on hard disk and now you can only boot with USB key inside.

am i assuming correctly that /dev/sdb is the USB disk? becausecause dev/sdc looks like restore partition (i sure hope you made backup of that one)

anyway one of the link i posted has an explanaiton what to watch for when installing ubuntu to external drive. if not there are also instruction on how to do it from virtual box.

point is you need to to boot into the OS somewhere for example from a DVD and then install to that USB disc. if you empt the disk (clear all partitions) then this should show as unallocated disk space. you can let the Ubutnu partition it but the important thing is again you must install grub there (on USB).

if you do it from virtualbox you could even have it so that the only drive it sees is USB.
for example: [http://www.youtube.com/watch?v=SnB4NrJrw3Q](http://www.youtube.com/watch?v=SnB4NrJrw3Q)
and author explaining the result: [http://www.youtube.com/watch?v=SnB4NrJrw3Q](http://www.youtube.com/watch?v=SnB4NrJrw3Q)

---

