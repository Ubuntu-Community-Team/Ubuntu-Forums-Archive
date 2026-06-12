---
title: "New to Linux/Ubuntu: Grub Error"
date: 2018-09-13
forum: New to Ubuntu
---

### Post by matt219 on 2018-09-13
Hello, so recently my girlfriends computer no longer wants to boot properly. Every time its turned on it does the initial load screen where you can open the boot menu or other options. But then it goes to the screen where it reads "grub error no such partition" and then enters rescue mode.

I tried to do some research and attempt to fix it myself even though I have no knowledge of linux or Ubuntu. When I run command "ls" I get: "(hd0) (hd0,msdos1) (hd1) (hd1,msdos2) (hd1,msdos1)". When I run command "set" I get: "prefix=(hd0,msdos5)/boot/grub     root=hd0,msdos5"

Now I've attempted the instructions and advice offered here:[https://askubuntu.com/questions/491604/grub-rescue-no-such-partition](https://askubuntu.com/questions/491604/grub-rescue-no-such-partition) 
But every time I get to the end where I run "insmod normal" im either met with "unknown filesystem" or "no such partition" (I get this when I run it with hd0,msdos5)

Her ex boyfriend built this computer and theres no way he would be willing to help us. And she doesn't believe she has the CD any more.

Its running windows 7.

Ill provide any additional information I can. But what do I need to do?

---

### Post by oldfred on 2018-09-14
Download current version of Ubuntu either 16.04 or 18.04 and create live installer.
       Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

Then boot in live mode and add Boot-Repair. Run the Summary report and post link it give to pastebin site, so we can review configuration and make suggestions.

       
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by matt219 on 2018-09-14
Thanks for responding oldfred. Here is the report

[http://paste.ubuntu.com/p/DCcs7gxyK7/](http://paste.ubuntu.com/p/DCcs7gxyK7/)

---

### Post by oldfred on 2018-09-14
It looks like  you have a newer UEFI system, but all drives are MBR(msdos).
Windows only boots from MBR partitioned drives with BIOS, so you are using CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
You show no Linux partitions, but have grub installed to MBR of sda.
You also show grldr which is grub4dos. That is used by EasyBCD to chain load to a Linux grub2 typcially, but no grub2 other than in MBR is shown.

Newer Windows typically uses a separate Boot partition which looks like your sdb1, but then it looks like you have the rest of the install in sda1. Normally boot partition and main partition ( c: drive ) are on same drive. And Windows boot loader is on that drive. 

Many then install Ubuntu to other drive. Or if an SSD, maybe both boot from SSD and have smaller system partitions on SSD, but lots of data on HDD drive.

What brand/model system?
Do you or really your girlfriend have good backups? Both Windows & from Ubuntu install?

It looks like their may be some space between sdb1 & sdb2? Could that be your old ext4 partition. It does not look large.
Did you run major Windows update. That often erases Linux partitions from partition table but data may still be there. If so try parted rescue or testdisk to see if there is a partition.

       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sdb > PT_sdb.txt
So you know sectors (actually info in report, but best to have backup):
sudo parted /dev/sdb unit s print 

      
 Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[URL="http://ubuntuforums.org/showthread.php?t=2315405"]http://ubuntuforums.org/showthread.php?t=2315405
      [/URL]
 GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html) 
    
       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
    
[URL="http://ubuntuforums.org/showthread.php?t=2315405"]
[/URL]

---

### Post by matt219 on 2018-09-15
What do you mean by brand/model of system? Sorry just need some clarification.
We have no back ups. Currently we are backing up all her photos and important documents/programs to a 500gb HDD.

Basically our end goal here is just to get the computer usable again for her, without her losing anything off of it. She's fine with having the PC only run windows. However she doesn't have the disks or program keys for her version of windows 7.

What is the best course of action to take if we want to just run windows on the PC and remove linux? Back all the important stuff onto the HDD and then run a clean install of windows?

Sorry I'm not the best with details. All of this is foreign to me and im just going with the info she's telling me. I appreciate your help so far though!

---

### Post by oldfred on 2018-09-15
You have to have the Windows product key to reinstall it. Or you have to buy a new copy.
Brand/model is whether Dell, Asus, HP, or whatever. Or motherboard if assembled yourself.

Since UEFI, it is a newer computer. Microsoft required all vendors to use UEFI/gpt for all computers starting with Windows 8 about 5 years ago. A few vendors started installing Windows 7 in UEFI mode to make sure UEFI worked before converting to Windows 8. But most Windows 7 installs on UEFI systems are where a user reinstalled Windows 7 overwriting/replacing the original Windows 8 and they did not convert Windows 7 installer to UEFI boot, so installed in BIOS boot mode and Windows converted drive from gpt to MBR.

       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

If it was downgraded, you still have a product key in your UEFI, but only for the OEM or vendor version. Some vendors will give you a new copy, most charge a nominal fee for the DVD. And a few just do not offer anything. The user is expected to make a backup.
And recovery partition on hard drive is useless when hard drive fails. So full backup of Window is always required. 

My Dell with Windows 8 wanted a Dell backup, a Windows backup and I made a full image backup with Macrium Reflect as soon as I got system. Had to go to store for more DVD & flash drives. And that system is only used with TV for watching DRM'd Comcast that does not work with Linux.

---

