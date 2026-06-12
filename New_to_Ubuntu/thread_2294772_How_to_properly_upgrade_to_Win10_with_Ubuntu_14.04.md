---
title: "How to properly upgrade to Win10 with Ubuntu 14.04 Dual Boot"
date: 2015-09-13
forum: New to Ubuntu
---

### Post by robertzito on 2015-09-13
My laptop is dual boot with windows 7 and ubuntu 14.04. I want to upgrade the win 7 side to win 10 and I have been reading how the upgrade over writes or removes grub. When looking at instructions on how to reinstall Grub it states that I need to know where linux is installed and where grub needs to be installed but this is all new to me so I am not sure based on the below fdisk -l is telling me. Can someone please help me to understand the below and what is what (which is ubuntu and where does grub go)? I have been reading and posts talk about MBR but I do not see that anywhere. 


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    28020735    13969408    7  HPFS/NTFS/exFAT
/dev/sda3        28020736  1039862240   505920752+   7  HPFS/NTFS/exFAT
/dev/sda4      1039863806  1953523711   456829953    5  Extended
/dev/sda5      1039863808  1937033215   448584704   83  Linux
/dev/sda6      1937035264  1953523711     8244224   82  Linux swap / Solaris

---

### Post by yancek on 2015-09-13
You won't see MBR in that type output as it lists partitions and the MBR is outside partitions.  It also shows that Linux is on /dev/sda5, see the 'Linux' at the far right of the line?  I don't see an EFI partition so it appears you have the older standard MBR method to boot so you would simply need to reinstall the Ubuntu Grub bootloader to the MBR pointing to sda5.  The windows update/upgrade will not delete (or should not delete) the Grub files on the partition with Ubuntu but will overwrite the code in the master boot record.  You will need the Ubuntu Live CD or flash drive to do this.  Detailed instructions on several methods of doing this are at the official Ubuntu site below starting at Section 2.2 on the right. 

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by Mark Phelps on 2015-09-13
Win7 machines, especially laptops, have been having serious problems upgrading to Win10, primarily because the Win10 Compatibility Checker does a lousy job of detecting hardware and/or driver problems in those machines.  I've had two laptops both fail the upgrade and the second was left in an unusable state, requiring restore from HP recovery media to get it working again.

If you're going to go down that route, then you should first image off your laptop partitions to an external drive.  Recommend using Clonezilla to clone the disk to an external disk.

---

### Post by robertzito on 2015-09-13
Honestly I do not want to take a chance because I have alot of time invested in this PC, I cloned my win8 in Virtual Box and ran the upgrade on it, all went well with no issues to report. I use the ubuntu side 99% of the time so why take the chance!

---

### Post by Mark Phelps on 2015-09-14
> **robertzito said:**
> Honestly I do not want to take a chance because I have alot of time invested in this PC, I cloned my win8 in Virtual Box and ran the upgrade on it, all went well with no issues to report. I use the ubuntu side 99% of the time so why take the chance!

You're not missing much -- really!  Without having new hardware designed for Win10, it's really little more than Win8.2 -- with a bunch of features moved around to new locations in the UI. OH, and they added a half-baked Start Menu -- for which there are much better free third-party alternatives.

---

### Post by Frogs Hair on 2015-09-14
> Win10 Compatibility Checker does a lousy job of detecting hardware and/or driver problems in those machines. I'm back to Win 7 on the laptop due to this problem I reverted fist and then preformed a factory reset.

---

