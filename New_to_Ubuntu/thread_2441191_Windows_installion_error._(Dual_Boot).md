---
title: "Windows installion error. (Dual Boot)"
date: 2020-04-20
forum: New to Ubuntu
---

### Post by canahmetdursun on 2020-04-20
Hey guys,
I have a problem. I had dual boot in my computer. Windows was in C and D. Ubuntu was in D but i had replaced my SDD. I want to install my windows again and update my Kubuntu 19.014 to Ubuntu 20.04. How can i do that? Thanks.
Note: I tried to boot up with usb but when i opened up windows installer it throws an error called ( Couldn't find any media driver)
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 19.04
Release:        19.04
Codename:       disco
*******************************
t
H/W path               Device     Class          Description
============================================================
                                  system         G5 5587 (0825)
/0                                bus            0M2MWX
/0/0                              memory         64KiB BIOS
/0/45                             memory         16GiB System Memory
/0/45/0                           memory         8GiB SODIMM DDR4 Synchronous 2667 MHz (
/0/45/1                           memory         8GiB SODIMM DDR4 Synchronous 2667 MHz (
/0/4e                             memory         384KiB L1 cache
/0/4f                             memory         1536KiB L2 cache
/0/50                             memory         9MiB L3 cache
/0/51                             processor      Intel(R) Core(TM) i7-8750H CPU @ 2.20GH
/0/100                            bridge         8th Gen Core Processor Host Bridge/DRAM
/0/100/1                          bridge         Xeon E3-1200 v5/E3-1500 v5/6th Gen Core
/0/100/1/0                        display        GP106M [GeForce GTX 1060 Mobile]
/0/100/1/0.1                      multimedia     GP106 High Definition Audio Controller
/0/100/2                          display        Intel Corporation
/0/100/4                          generic        Xeon E3-1200 v5/E3-1500 v5/6th Gen Core
/0/100/8                          generic        Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7
/0/100/12                         generic        Cannon Lake PCH Thermal Controller
/0/100/14                         bus            Cannon Lake PCH USB 3.1 xHCI Host Contr
/0/100/14/0            usb1       bus            xHCI Host Controller
/0/100/14/0/2                     input          SteelSeries Rival 600
/0/100/14/0/5                     multimedia     Integrated_Webcam_HD
/0/100/14/0/9                     communication  Goodix Fingerprint Device
/0/100/14/0/e                     communication  Bluetooth wireless interface
/0/100/14/1            usb2       bus            xHCI Host Controller
/0/100/14/1/1          scsi2      storage        Cruzer Glide 3.0
/0/100/14/1/1/0.0.0    /dev/sdc   disk           15GB Cruzer Glide 3.0
/0/100/14/1/1/0.0.0/0  /dev/sdc   volume         14GiB Windows FAT volume
/0/100/14.2                       memory         RAM memory
/0/100/14.3            wlp0s20f3  network        Wireless-AC 9560 [Jefferson Peak]
/0/100/15                         bus            Intel Corporation
/0/100/15.1                       bus            Intel Corporation
/0/100/16                         communication  Cannon Lake PCH HECI Controller
/0/100/17                         storage        Intel Corporation
/0/100/1b                         bridge         Cannon Lake PCH PCI Express Root Port 2
/0/100/1d                         bridge         Intel Corporation
/0/100/1d/0            enp59s0    network        Killer E2400 Gigabit Ethernet Controlle
/0/100/1f                         bridge         Intel Corporation
/0/100/1f.3                       multimedia     Cannon Lake PCH cAVS
/0/100/1f.4                       bus            Cannon Lake PCH SMBus Controller
/0/100/1f.5                       bus            Cannon Lake PCH SPI Controller
/0/1                   scsi0      storage        
/0/1/0.0.0             /dev/sda   disk           1TB ST1000LM035-1RK1
/0/1/0.0.0/1           /dev/sda1  volume         15MiB reserved partition
/0/1/0.0.0/2           /dev/sda2  volume         736GiB Windows NTFS volume
/0/1/0.0.0/3           /dev/sda3  volume         487MiB Windows FAT volume
/0/1/0.0.0/4           /dev/sda4  volume         48GiB EXT4 volume
/0/1/0.0.0/5           /dev/sda5  volume         27GiB Linux swap volume
/0/1/0.0.0/6           /dev/sda6  volume         118GiB EXT4 volume
/0/2                   scsi1      storage        
/0/2/0.0.0             /dev/sdb   disk           256GB LITEON CV8-8E256
/0/2/0.0.0/1           /dev/sdb1  volume         238GiB Windows NTFS volume
/1                                power          DELL W7NKD86
/2                     docker0    network        Ethernet interface


```

---

### Post by oldfred on 2020-04-20
Linux does not use partition descriptions like D:.
You have a newer UEFI system, but description sounds like your installs are/were the 35 year old BIOS/MBR configuration.

Windows only installs in UEFI boot mode to gpt partitioned drives.
Windows only installs in old BIOS boot mode to MBR partitioned drives.
Ubuntu does not care but needs to be installed in same boot mode as Windows and can be on gpt in BIOS boot mode.
With your newer UEFI system, both systems really should be UEFI installs.

Post this:
sudo parted -l

Both Windows & Ubuntu install in boot mode you use to boot install media. If you boot Ubuntu or Windows in UEFI mode but drive is old MBR, it will either erase it, or convert it to gpt erasing it. You can convert a drive with gdisk, but partition requirements are different.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by canahmetdursun on 2020-04-20
> **oldfred said:**
> Linux does not use partition descriptions like D:.


I meant disk1 sorry.

```

 
Model: ATA ST1000LM035-1RK1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  17.8MB  16.8MB                  Microsoft reserved partition  msftres
 2      17.8MB  790GB   790GB   ntfs            Basic data partition          msftdata
 3      790GB   791GB   512MB   fat32                                         boot, esp
 4      791GB   843GB   52.0GB  ext4
 6      843GB   970GB   127GB   ext4
 5      970GB   1000GB  29.9GB  linux-swap(v1)


Model: ATA LITEON CV8-8E256 (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  256GB  256GB  ntfs               msftdata


Error: /dev/sdc: unrecognised disk label
Model: SanDisk Cruzer Glide 3.0 (scsi)                                    
Disk /dev/sdc: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 



```

---

### Post by oldfred on 2020-04-20
That is then UEFI install to gpt partitioned drive with the FAT32 esp partition.
Your 19.04 is EoL - End of Life. You need to install 18.04LTS or soon to be released 20.04LTS.
And be sure to boot both Windows & Ubuntu in UEFI boot mode to install in UEFI boot mode.

See link in my signature for Ubuntu UEFI install info.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 

Did you boot Windows in UEFI mode, it only will install to gpt with UEFI.

---

### Post by canahmetdursun on 2020-04-20
So first i need to install a LTS version of ubuntuin uefi mode. Right? Sorry i am a newbie :)

---

### Post by oldfred on 2020-04-20
With UEFI it is not as critical whether you install Windows or Ubuntu first.
Is it sdb that you want to install Windows into?
Will Ubuntu also be on same drive?
I would still install Windows first to a blank SSD, as it wants lots of partitions as link in post #2 above shows.
If you just have one NTFS partition not sure if Windows will install?
I would then shrink the main c: drive Windows partition using Windows tools to make space for Ubuntu. But use gparted or installer to create Linux partitions.
If using HDD for data I might have /home and/or large data partition(s) on HDD. One NTFS for any shared data, perhaps media and ext4 for /home or Linux data. 
Your Ubuntu / (root) does not have to be large if /home or your data are on separate partitions.

---

### Post by canahmetdursun on 2020-04-20
I want to install Windows but it throws error.
I want to install my Windows in my fresh SSD.
No Ubuntu will in my HDD.
How can i solve this error? I think it all done ? Because every partition looks good.

---

### Post by Impavidus on 2020-04-20
(Didn't read your last post before writing this.)

One addition to oldfred's excellent comments: a 30GB swap partition is very large. I don't know how you want to use your storage, but typically 4GB swap, 30GB root and everything else /home or data is enough. Nowadays it's standard to use a swap file (which will be on the root partition), but you can still use a swap partition if you prefer (I do).

---

### Post by yancek on 2020-04-20
Read the first link in post 4 above by oldfred which explains and is the official Ubuntu documentation on dual booting with windows 10 UEFI.  Simpler to install windows first.  If you can't boot the windows installer from the usb, you should post the exact error.  Is it could not find media or could not find a driver?  Also, you will have a lot better luck trying to resolve your failure to boot the WINDOWS installer at a WINDOWS forum or the microsoft site.

I'm having difficulty understanding what you are referring to in your last post.  Are you getting the same error trying to install windows as you mention in your first post?  What does "every partition looks good" mean?  Your posts indicate you have not yet installed anything to the SSD.  Do you still have windows and Kubuntu on the original drive?

---

### Post by canahmetdursun on 2020-04-20
Thanks about that swap hint! In an article i had read that swap partition should be : your RAMs x2. So i made it 30. :) But i will do it 4GB as you said.

---

### Post by canahmetdursun on 2020-04-20
I meant by saying that i have all the capacity for a Windows and Ubuntu. 
I have not installed anything to the SSD. 
I don't have windows and kubuntu at the same drive.

---

### Post by oldfred on 2020-04-20
Both drives show large NTFS partitions.
Having one large NTFS may interfere with the auto partitioning that Windows wants to do.
I would also disconnect or in UEFI change drive setting for large drive to disabled, so Windows installer will not see it.
You may have to reinstall grub or use efibootmgr to add back entry into UEFI. UEFI forgets entries when a drive is disconnected.

---

### Post by canahmetdursun on 2020-04-20
Cool idea thanks.
Btw ubuntu throws me an error that called 10. Faulty in cd dvd or hdd.

---

### Post by canahmetdursun on 2020-04-20
And i am getting initframs unpacking failed

---

### Post by oldfred on 2020-04-20
Check that your downloaded ISO is correct.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Some just have tried different tools to create installer, some have tried different flash drives and others just redo it and it works.

---

### Post by Impavidus on 2020-04-21
> **canahmetdursun said:**
> Thanks about that swap hint! In an article i had read that swap partition should be : your RAMs x2. So i made it 30. :) But i will do it 4GB as you said.

Yes, that was the rule 15 years ago, when RAM was about 1GB. A lot of old recommendations, no longer valid, can still be found on the web.

---

### Post by canahmetdursun on 2020-04-21
Getting these errors... on Ubuntu 19.10 ```
nouveau 0000:01:00.0: secboot: error during falcon reset: -110
Failed to start GNOME Shell on X11.
xhci_hcd 0000:3a:00.0: HC died; cleaning up
```

---

### Post by CelticWarrior on 2020-04-21
```
Failed to start GNOME Shell on X11
```

This is because you have a Nvidia Graphics not properly supported by the open-source driver *nouveau* (see the preceding error message) therefore you need to add 'nomodeset' to have a desktop environment in the live session and then install as usual. make sure to select the option to install third-party drivers, codecs, etc.

How to add nomodeset?
In the first menu (Grub) with the "Try Ubuntu" option selected, press 'e' to edit. Use the cursor keys to navigate to where "quiet splash" is and add "nomodeset" after it. Confirm and proceed. It should now boot the live session with low graphics.

---

### Post by canahmetdursun on 2020-04-21
Firstly , I found that my hdd has 120 bad sectors. Should i fix it first ?

---

### Post by CelticWarrior on 2020-04-21
> **canahmetdursun said:**
> Firstly , I found that my hdd has 180 bad sectors. Should i fix it first ?

Bad sectors aren't fixable.

---

### Post by canahmetdursun on 2020-04-21
@CelticWarrior 
nvidia problem solved thanks.

---

### Post by canahmetdursun on 2020-04-21
[URL="https://paste.ubuntu.com/p/RrpFgXQ29m/"]


https://paste.ubuntu.com/p/RrpFgXQ29m/[/URL]
Error hell...

---

### Post by oldfred on 2020-04-21
How did you get Ubuntu as the Windows boot manager? That was an alternative way to boot many years ago with early UEFI.
And had not been done nor recommended for years.

```
efibootmgr -v
=============
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0003,0000,0004,0005
Boot0000* [COLOR=#ff0000]Windows Boot Manager[/COLOR]    HD(2,GPT,fd2acfaf-8f91-45df-aca2-351d7b0fdf17,0x8800,0x5c05e800)/File([COLOR=#ff0000]EFIubuntugrubx64.efi[/COLOR])WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0003* ubuntu    HD(1,GPT,5aaa69fb-d979-4bf9-a86c-30c1a78554c1,0x5c067800,0x64000)/File(EFIubuntushimx64.efi)
Boot0004* UEFI: SanDisk    PciRoot(0x0)/Pci(0x14,0x0)/USB(17,0)/CDROM(1,0x3e26a4,0x7c00)..BO
Boot0005* UEFI: SanDisk, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(17,0)/HD(2,MBR,0x6132549e,0x3e26a4,0x1f00)..BO
```

You have to delete entry 0000 and create new Windows UEFI boot entry with efibootmgr.
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

And the GUID in the Windows UEFI boot entry is not for an ESP, but for your Windows NTFS partition. That will never work.
You have to have Windows boot loader installed into the UEFI. Did you manually create that entry? Or how?

It looks like at minimum you need a full set of Windows repairs with Windows repair disk or installer's repair console or a total reinstall of Windows.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by canahmetdursun on 2020-04-22
Cleaned UEFI.


```
efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0003,0004,0005
Boot0003* ubuntu    HD(1,GPT,5aaa69fb-d979-4bf9-a86c-30c1a78554c1,0x5c067800,0x64000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* UEFI: SanDisk    PciRoot(0x0)/Pci(0x14,0x0)/USB(18,0)/CDROM(1,0x3e26a4,0x7c00)..BO
Boot0005* UEFI: SanDisk, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(18,0)/HD(2,MBR,0x6132549e,0x3e26a4,0x1f00)..BO


```

I don't know how i did/created that. I guess windows.iso makes it.  I didn't install Windows on. 
Should i do an UEFI boot partition in first disk which where i will install windows on ?

---

### Post by oldfred on 2020-04-22
windows will want an ESP, if installing to gpt partitioned drive and booting installer in UEFI boot mode.
But it likes either unallocated drive or full set of partitions.
And in may install to whatever drive is seen as default drive in UEFI settings. Often better to disable or physically disconnect other drives. But UEFI forgets UEFI boot entries, so you may need Ubuntu live installer to reinstall grub or just use efibootmgr to recreate Ubuntu entry in UEFI.

See post #2 above or the partitions that Windows creates for UEFI boot systems.

---

### Post by CelticWarrior on 2020-04-22
I've done multiple Windows installations after Ubuntu, in UEFI, to a different drive than the one containing the ESP. No problem whatsoever. Of course it changes the boot order to itself but it's just a matter of making Ubuntu first in line again. It doesn't mess with the Ubuntu partitions or efi files.

---

### Post by canahmetdursun on 2020-04-26
I tried to disable my HDD in bios and i checked with diskpart. Yes i disabled it but same error occurs...

---

### Post by oldfred on 2020-04-26
Boot-Repair showed grub reinstall with error 0 which is no error.
So are issues just with Windows?
If so, a Windows forum may know more.
We can usually help on minor issues or dual boot issues, but plain Windows install that does not work is not normal.

---

### Post by canahmetdursun on 2020-04-27
I'll try to open up windows install manager in virtual machine. Maybe the iso image is corrupted or so... or outdated. i dont know.

---

### Post by canahmetdursun on 2020-04-27
SOLVED! yaaaaaaaaaaaaaaaaaaaaaay. 
It's been a week. Damnn. 
SOLUTION : 
Create a WINDOWS 10 OS on virtual machine.
Then install WINDOWS INSTALLATION TOOL. 
Create a bootable USB stick.
Reboot n press F12.
All done.

---

