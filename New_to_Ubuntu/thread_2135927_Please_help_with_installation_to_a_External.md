---
title: "Please help with installation to a External?"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by DigiDuncan on 2013-04-15
Here's my issue: I consider myself a nerd, but not a coder. I, for Christmas, got a Windows 8 (64 bit) laptop, a Lenovo g585, and have loved the freedom of a personal PC. Now, however, I feel the bulkiness and mere unusability of it has gotten to me. I have a USB 3.0 2TB Western Digital Hard Drive (platters), and want to install to that. This is my first time Linuxing, and I'm not sure what the problem here is. It does not recognize my External USB Drive as a drive it can install to, which is troubling because I have a tiny internal (250GB), and this is a laptop. If anyone could help me out, I would be extremely appreciative. 

Thanks! :mrgreen:
~DigiDuncan

EDIT:
Let me clarify some stuff.
I have a 2TB Western Digital External USB 3.0 Laptop Drive [http://www.officedepot.com/a/product...Media-_-793348]("http://www.officedepot.com/a/products/793348/Western-Digital-My-Passport-Portable-USB/?Channel=Google&mr:trackingCode=E295AD9A-2FBD-E111-A306-001517384FBA&mr:referralID=NA&mr:adType=pla&mr:ad=22395426956&mr:keyword=&mr:match=&mr:filter=20224360076&cm_mmc=Mercent-_-Googlepla-_-Technology+Data_Storage_Media-_-793348")
I have a Lenovo G585 Laptop, Windows 8 64 Bit. [http://www.lenovo.com/products/us/te...g-series/g585/]("http://www.lenovo.com/products/us/tech-specs/laptop/essential/g-series/g585/")
I would like two partition 500 GB for Ubuntu and related, and 1.5 TB for  file storage, along with read/write using BOTH Win8 and Ubuntu. This  will be mainly .avi reading/writing for YouTube recordings.
The Ubuntu will not recognize the External hard drive for installing Linux to.
Basically, I want to be able to, if the HD is plugged in, boot to either Linux or Windows, but still use the HD for storage.
Sorry for the confusion!
Thanks!

EDIT 2: Solved! Thanks /u/oldfred!

---

### Post by zemega on 2013-04-15
For starter, I'm sure you will have spare USB drives around. Look up Unetbootin. This program will allow you to try Live version of any supported Linux. You need the ISO as well. Run the program and you can choose whether to put the Live version into the USB drive or your external. Then just make sure you boot from the option you choose (check the BIOS or EUFI settings). If you can boot from the external, you can just install directly using the live version. You can choose whether to format, partition and which filesystem you want to use.

A side note, Windows 8 hate Linux. So, from your post, you recieve one or two laptop?. You need to configure the booting through BIOS/UEFI. If you plan to run Linux just from your external, that is not a problem, you can just set your boot sequence into something like this 1:USB 2:HDD. 

Another note is filesystem. While most Linux uses ext4/3, you can always use other file system such as FAT. The only complication is I don't know whether Windows 8 will be friendly to ext3/4, previous version certainly not. So if you format you whole external into ext3/4 it will be sort of useless (not really, the are bypass), you cannot easily use the external with Windows (you might be able to read the external using programs, but writing will be hard). So, my best advice, is to partition that external into several partition, where one is in ext3/4 for your Linux OS, and others in either NTFS or FAT. Well, you can just always use FAT for your Linux installation. But I'll let someone that really knows about the filesystem elobarates on this.

---

### Post by oldfred on 2013-04-16
If you have Windows 8 pre-installed system then you are booting with UEFI with secure boot. And drives have to be partitioned with gpt not the old (ancient) MBR(msdos) partitioning scheme.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

Only a few users have UEFI dual boots. You could force install to MBR on external but would have to go into UEFI/BIOS each time to and change from or to UEFI to boot Windows and BIOS to boot UBuntu.

      
 Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

Since it is an external drive you need to have efi partition with gpt partitioning on external drive. If you have data and it is MBR, be sure to back that up as reformatting to gpt will erase all data.
There may be a way to convert, but I have never done it.
      
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by afz12 on 2013-04-16
DigiDuncan; I tried installing Ubuntu 12.04 etc. to a 500 GB USB hard drive some months ago. It seemed straightforward and I certainly didn't need to use any special Linux tricks. The drive started as NTFS and the CD ISO image did the necessary formatting to ext4 etc. After that, I could boot into the external USB OS or the notebook OS's. Unfortunately I don't remember the exact steps, but for me they certainly would not have been advanced or unusual! However, I am not suggesting the advice of other posters should be ignored of course - their expertise will surely exceed mine.  :)

---

### Post by zemega on 2013-04-16
Its certainly simple if you have no intention in using the external with other OS, particularly Windows. You will need third party programs to read such as in here [http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/) even then writing is not advised. I would like OP to know the love-hate interaction between Windows and Linux, and make choices.

---

### Post by DigiDuncan on 2013-04-16
Let me clarify some stuff.
I have a 2TB Western Digital External USB 3.0 Laptop Drive [http://www.officedepot.com/a/products/793348/Western-Digital-My-Passport-Portable-USB/?Channel=Google&mr:trackingCode=E295AD9A-2FBD-E111-A306-001517384FBA&mr:referralID=NA&mr:adType=pla&mr:ad=22395426956&mr:keyword=&mr:match=&mr:filter=20224360076&cm_mmc=Mercent-_-Googlepla-_-Technology+Data_Storage_Media-_-793348](http://www.officedepot.com/a/products/793348/Western-Digital-My-Passport-Portable-USB/?Channel=Google&mr:trackingCode=E295AD9A-2FBD-E111-A306-001517384FBA&mr:referralID=NA&mr:adType=pla&mr:ad=22395426956&mr:keyword=&mr:match=&mr:filter=20224360076&cm_mmc=Mercent-_-Googlepla-_-Technology+Data_Storage_Media-_-793348)
I have a Lenovo G585 Laptop, Windows 8 64 Bit. [http://www.lenovo.com/products/us/tech-specs/laptop/essential/g-series/g585/](http://www.lenovo.com/products/us/tech-specs/laptop/essential/g-series/g585/)
I would like two partition 500 GB for Ubuntu and related, and 1.5 TB for file storage, along with read/write using BOTH Win8 and Ubuntu. This will be mainly .avi reading/writing for YouTube recordings.
The Ubuntu will not recognize the External hard drive for installing Linux to.
Basically, I want to be able to, if the HD is plugged in, boot to either Linux or Windows, but still use the HD for storage.
Sorry for the confusion!
Thanks!

---

### Post by alhefner on 2013-04-16
I used this to get my [dual boot on external hard]("http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/") drive going.

---

### Post by oldfred on 2013-04-16
See the link already posted above to a user who did something similar in that he installed to sdc with UEFI and gpt partitioning.
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)

You need to have an efi partition on the externel drive if you every want to separately boot it, but grub/Ubuntu will probably install boot files into the efi internal drive's partition which will not cause any issues with Windows. Not like a dual boot BIOS/MBR at all.

I would suggest this:
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
    
I do not think you will need /home to be 500GB and would just make your NTFS shared data partition larger. 
       
I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. If you have any data on external back it up first at changing partitioning will erase ALL data. If you have no other way there is a program to convert but I have never used it.

---

