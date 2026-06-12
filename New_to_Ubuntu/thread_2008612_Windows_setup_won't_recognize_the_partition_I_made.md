---
title: "Windows setup won't recognize the partition I made for it"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by motoroller on 2012-06-22
Hey everyone,

I've been using Ubuntu 11.10 for several months now and I'm loving it, but unfortunately there are a few games I want to play that seem to insist on running on windows. I've tried WINE with some success, and it works... sort of... For simple applications I just use VirtualBox, but many games completely overtax its resources, so VB isn't an option here.

I just got a new HDD with the intention of making a partition for windows XP and some games, so I can use Ubuntu most of the time, but if I want to play a certain game, I can just boot into windows and start playing. 

I used gparted to partition my 500gb HDD into 400gb ext4 and 100gb NTFS partitions. I figured this would be fine, so I popped in the windows setup disc and booted from that. The setup went ok until the point when it asked me where to install windows. All that showed up were my physical hard drives, with NO mention of any partitions.

I know people dual-boot all the time, so what am I missing here? Your help is greatly appreciated!

---

### Post by oldfred on 2012-06-22
Is NTFS a primary partition or sda1 thru sda4? 

Did you put boot flag on the primary NTFS partition. Windows only installs, repairs or boots from "active" partition which we see as boot flag.

Post this 
```

sudo fdisk -lu
```

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

Or if you want a gui to repair boot:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by motoroller on 2012-06-23
> **oldfred said:**
> Is NTFS a primary partition or sda1 thru sda4? 

Did you put boot flag on the primary NTFS partition. Windows only installs, repairs or boots from "active" partition which we see as boot flag.

Post this 
```

sudo fdisk -lu
```How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

Or if you want a gui to repair boot:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

My NTFS partition is not the primary-- it's on sdb2. Also, how would I go about putting a boot flag on this partition?

here's the output from fdisk....

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002a950

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   117229567    58613760   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24d524d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24d524d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   160086527    80043263+  ee  GPT


thanks for your help

---

### Post by oldfred on 2012-06-23
Windows XP will not work on gpt partitioned drives, neither boot nor read. You need to totally reformat to MBR with gparted and in gparted right click to set boot flag. If an SSD gpt is the preferred way to format. Also in BIOS XP needs extra drivers to work with AHCI. I have XP on a old MBR drive, use gpt with BIOS for my Ubuntu drives & new SSD drive. But since SSD and AHCI, it is a real hassle to boot XP as I have to reset BIOS. Or I do not boot XP. :)

And Vista/7 will only boot from gpt drives if UEFI, but will read data from gpt drives.

---

### Post by motoroller on 2012-06-23
Ok what I did was take my smallest physical drive (80gb) and reformat it as MBR with one NTFS primary partition. 

I ran Windows XP setup and it DID recognize the drive (as drive C) and would have installed it, but when I selected it as the target volume, I got the following message:

"To install Windows XP onto this drive, setup must write some startup files to the following disk..." referring to my 60gb SSD that I use for booting Ubuntu. Then says "however, this disk does not contain a Windows XP compatible partition".

So here's the thing... According to fdisk and gparted, this 60gb SSD is in MBR, although formatted as ext4. Would I need to create a small NTFS partition here in order to install windows? or is there something I can mess with in my BIOS? (by the way, my BIOS is an ASUS UEFI and easy to configure...)

Man, windows doesn't like to play well with others :mad:!

---

### Post by oldfred on 2012-06-23
I did not think XP did that, but have seen where Windows 7 installs its boot partition to sda even when installing to sdb or sbc.
Try reseting BIOS so that BIOS boot drive is the drive you are installing Windows into, so it will install its MBR to that drive.

IF you converted SSD to MBR and fdisk still reports it as gpt then you have a partially converted drive. gpt has a backup partition table at the end of the drive. Windows only deletes the primary partition table when it converts from gpt to MBR and ignores the backup. Linux tools see the backup and think it is gpt but may get confused as it also has the MBR data.

 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by motoroller on 2012-06-23
> **oldfred said:**
> I did not think XP did that, but have seen where Windows 7 installs its boot partition to sda even when installing to sdb or sbc.
Try reseting BIOS so that BIOS boot drive is the drive you are installing Windows into, so it will install its MBR to that drive.

IF you converted SSD to MBR and fdisk still reports it as gpt then you have a partially converted drive. gpt has a backup partition table at the end of the drive. Windows only deletes the primary partition table when it converts from gpt to MBR and ignores the backup. Linux tools see the backup and think it is gpt but may get confused as it also has the MBR data.

 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt


I tried using fixparts and it confirmed that the MBR on this old HDD (sdc) was ok, and here's the output:

Loading MBR data from /dev/sdc

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 160086528 sectors (76.3 GiB)
MBR disk identifier: 0x00083DFF
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048    160086015   primary     Y        Y      0x07

MBR command (? for help): 


So everything looks to be in order here... I'm kind of stumped. I tried going into my BIOS boot menu and selecting my 80gb HDD (sdc) as the boot drive, but then it just said something to the effect of "no bootable system found on this drive" and I had to restart. Hmm.....

---

### Post by oldfred on 2012-06-23
You want to set BIOS to boot from drive you plan to install Window into, so it thinks that is sda.

---

### Post by motoroller on 2012-06-23
> **oldfred said:**
> You want to set BIOS to boot from drive you plan to install Window into, so it thinks that is sda.

Well I'll be damned! It worked! I owe you a beer :D

This whole experience made me appreciate how easy and straightforward installing Ubuntu was...

---

### Post by oldfred on 2012-06-24
Glad you got it working.

I will be over tomorrow to collect. :).

---

