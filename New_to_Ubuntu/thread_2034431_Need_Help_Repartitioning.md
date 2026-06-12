---
title: "Need Help Repartitioning"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by velkypivo on 2012-07-28
I have Grub2 bootable sda with Windows on it, and also a failed Linux Mint installation alongside it on sda5 and 6. Also have sdb with nothing on it, and currently non-bootable sdc (boots from sda Grub2) with nicely working Linux install.
Actually, fdisk -l shows asterisk under bootable for sdc but it will not boot since it loads from sda, I guess.



1) I want to remove non-functioning 20GB Linux file system and swap from extended partitions sda5 and 6, and pray that it will leave my Windows intact, and will still boot Windows afterwards. Also need to resize NTFS partition to maximum without loosing anything. Also, maybe remove unwanted Grub boot menu entries before that ?
 

 2) I would also like to make my sdc bootable (it boots from sda now),  
 

 This way I will have both drives bootable: sda - Windows only, sdc - Linux only
 

 I do not want to damage Windows (lotsa expensive programs installed, but do not have installers any longer). If that happens I am dead.
 

 Since Linux Mint Julia (Ubuntu kernel) is running nicely on sdc I do not want to loose that either.
 

 I had not so good previous experience with Grub. Then there is also gparted with ntfs utilities, and kde partition manager, and Windows disk stuff. 

Can you please help ?
 

 Some more HD info might help:

Device Boot Start End Blocks Id System
/dev/sda1 * 1 16704 134174848+ 7 HPFS/NTFS
/dev/sda2 16705 19458 22114305 5 Extended
/dev/sda5 16705 19197 20018176 83 Linux
/dev/sda6 19197 19458 2095104 82 Linux swap / Solaris

Device Boot Start End Blocks Id System
/dev/sdb1 1 9965 80041984 b W95 FAT32

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 120837 970616832 83 Linux
/dev/sdc2 120837 121602 6142977 5 Extended
/dev/sdc5 120837 121602 6142976 82 Linux swap / Solaris

---

### Post by Mark Phelps on 2012-07-28
Need to know first if this is Windows 7 you are running.  Because, if it is, I would start by doing the following:
- Disconnect all but the Windows drive
Can you now boot into Win7 with only that drive connected? If so, skip to the Remove Partitions info below.
If you can't boot into Win7, then reconnect the other drives and boot into Win7 that way.
- Use the backup feature to create and burn a Win7 Repair CD.
- Shut down the PC
- Disconnect all but the Windows drive
- Boot from the Win7 Repair CD
- Run Startup Repair three times -- that's right, three times

When done, you should be able to boot directly into Win7 using only that drive, and without the CD.

Remove Partitions: ............

You can either (a) boot into Win7 and use the Disk Management utility to remove the partitions, or (b) boot using an Ubuntu LiveCD and use GParted to remove the partitions.

Resize the Windows Partition: ...

The safest way to do this is to boot into Win7 and use the Disk Management utility to (a) remove the Extended partition and (b) resize the Win7 partition.  You CAN do this using GParted, but that risks corrupting the Win7 boot loader -- something you don't want to risk.

OPTIONAL WAY: .....

Personally, if it was MY pc, instead of having the Win7 partition take up the whole drive, I would create another NTFS partition to fill the drive and use that as a shared Data partition.

Ubuntu and Linux Mint -- sorry, don't use Mint enough to know how to make SDC bootable without removing bootability of Linux Mint.

---

### Post by oldfred on 2012-07-28
You can run fixMBR from a Windows repair console to reinstall the Windows boot loader to the MBR. Windows uses the boot flag to know what partition to boot from.  You can use gparted to delelete the obsolete partitions, but use the Windows partition tools if Windows 7 (or Vista) to expand the NTFS partition. It will want to run chkdsk after a size change.

If you have not made a Windows repairCD or USB:
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

For sdc you can just install the grub2 boot loader to sdc and set BIOS to boot from it.

Be sure your Ubuntu liveCD is the same version as your install. You can add this into your boot of the liveCD/USB or download a full liveCD as a repair CD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

If you can boot into Ubuntu you can easily install grub2's boot loader to sdc.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdc but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck /dev/sdc
sudo update-grub

But grub also remembers where to reinstall on major updates, so you may want to check where it will reinstall and update it if necessary.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by velkypivo on 2012-07-28
It is Windows 2000 

(as I said lotsa programs there, that won't run on  XP, Vista, 7 unless I spend thousands to get major upgrades)

---

### Post by oldfred on 2012-07-28
I am surprised that if it is Windows 2000 based software that you cannot find equal or even better equivalents in Linux for free.

From XP I found most software was as good or good enough if not quite as good. I understand those with games wanting Windows and a fast computer, but most users can use Linux for the vast majority of common tasks.

The Windows boot loader in the MBR has not changed. All it does is look for the primary partition with the boot flag and jump to that to continue to boot. You can install Windows or many other boot loaders like lilo or syslinux (but just the MBR part) that do the same to boot and they will boot Windows.

---

### Post by velkypivo on 2012-07-29
Having the W2K on sda, does it make a difference in above procedures ?



Sidenote to program availability:

Not even close in Linux case. These are specialized engineering applications.

Some upgrades exist for XP or Vista or 7 but we are talking about  > $100k to switch over to upgrades. I don't have access to that kind of $$$ any longer.

---

### Post by oldfred on 2012-07-29
Windows always seems to work better if it is sda & the first partition, but it does not have to be.

Updates should be fine with Windows in sda.

---

### Post by velkypivo on 2012-08-03
Used gparted from sdc to delete partition of messed up Maya installation on sda.
Then used easeUS from Windows on sda to merge/resize freed up partition with existing Windows partition without any data loss.
Then used easeUS to knock out Grub from sda and to put Windows MBR in there instead.
Worked flawlessly.

---

