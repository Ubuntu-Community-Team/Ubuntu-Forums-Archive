---
title: "using Boot-repair to reinitialize Grub"
date: 2016-02-05
forum: New to Ubuntu
---

### Post by Pete_Wilson on 2016-02-05
I am a total newbie to Ubuntu and Linux (tired of M$).  I have made a pastebin link @ [http://paste.ubuntu.com/14894497/](http://paste.ubuntu.com/14894497/).  I used the Recommended repair option and It left me with a screen that gives me the option to install ubuntu. I have already installed Ubuntu and don't want to reinstall but use my existing installed OSes.   Right now I am running off of USB.  I have access to my 5 M$ OSes with a work around but I don't know where to go in the special options to repair my Grub boot sector so that I have access to all the OSes by Grub.  Thanks for the assistance.

---

### Post by oldfred on 2016-02-05
Do not run autofix. 
That just installs grub to the MBR of every drive.
It will give an error if it attempts to install grub to sde as you do not have a bios_grub partition.

But you really want to keep the Windows boot loader on sda, as all you Windows boot from sda1. In sda1 you show both the old XP boot files and newer bootmgr and BCD for newer Windows. All Windows installs use the BIOS default drive's partition with the boot flag to install its boot files. Generally then all installs use only one boot partition.

You just want grub installed to sdf, and change BIOS to boot from drive that is sdf. Use Boot-Repair's advanced options to choose Ubuntu install in sdf1 and choose MBR of sdf to install grub2's boot loader.

You have an issue that may be interfering with everything as all partition tables generally are read to see all the drives.
```
/dev/sda4         146,223,104 1,465,144,064 1,318,920,961   f W95 Extended (LBA)
Extended partition linking to another extended partition.
/dev/sda5         146,225,152   524,664,831   378,439,680   7 NTFS / exFAT / HPFS
```

I do not see the specific issue it is complaining about.

You can try this:
 sudo fdisk /dev/sda

   Press "w". That rewrites the partition table.

---

### Post by Pete_Wilson on 2016-02-05
Thanks for the prompt response.  I have read your reply several times and I have some questions. I presume that the code that you pasted into the reply is from the pastebin link.  Is there a way that I can view this code?  I have done two pastebins here is the other link  [http://paste.ubuntu.com/14885215/](http://paste.ubuntu.com/14885215/)  .  The sequence is that the 14885215 is an earlier pastebin prior to any activity (I think) in my use of Boot-repair.  I did run autofix after the first pastebin now the only way I can get to the windows installation is by booting directly from /dev/sda.  I guess that the MBR of sda has not been over written.  It is my understanding that if I want to use Ubuntu that I have to use Grub and I have to allow Grub to give me the option to choose which OS to boot into.  If I load Grub only on sdf  and select the drive at Boot time that will be the boot loader how do I revert the other drives that have been written to by boot-repair.  
Your statement after your code paste "[COLOR=#000000]I do not see the specific issue it is complaining about.[/COLOR]

[COLOR=#000000]You can try this:
[/COLOR]
[COLOR=#000000]sudo fdisk /dev/sda[/COLOR]

[COLOR=#000000]Press "w". That rewrites the partition table." 
[/COLOR]Indicates to me that there is something in the code that is problematic.  Could you explain to me what it is that you see that causes you to think that there is a complaint.  Does the command <[COLOR=#000000]sudo fdisk /dev/sda[/COLOR]> have the capability to fix the "specific issue" beyond it's ability to rewrite the MBR and restore the ability to boot into windows boot loader.
I hope that I have been clear with my questions as I don't want to screw up this system any furter but I do want to learn a Linux OS as I have had it with Micro$oft.  I don't want be a bother but I do want to learn the underlying concepts.

---

### Post by yancek on 2016-02-05
Your paste bin output shows you have 7 drives, 6 of which have windows code in the MBR, none of which have any Grub code and one drive (sd3) with nothing in the MBR.  Your Ubuntu is installed on sdf1 so you should have selected to install Grub to /dev/sdf during the installation.  You would then have to select that drive to boot from the BIOS on boot.  You will have that option with the manual (Something Else) option during the install.  Is that the option you used?  You could also install Grub to /dev/sda, the MBR of the first drive which would overwrite the windows code for that drive and if all goes well, create menuentries for your other operating system.  Not sure what you want to do?

---

### Post by oldfred on 2016-02-06
If grub was installed to sda, I would reinstall grub to sdf. And install a Windows boot loader to sda. 
Grub only boots working Windows, so when Windows breaks, you may be able to directly boot from BIOS or one time boot key and use f8. Otherwise use a Windows repair disk or install disk to get into repair console.

You can use Boot-Repair to install a Windows boot loader to sda. It installs syslinux which works like Windows boot loader. Or you can use a Windows repair disk and use fixMBR.l

If you look at line 200 in pastebin link you see the error on linked partition. 
The fdisk command rewrites partition table and should correct it.

May be best to back up partition table entries to a file and copy to another drive first, just in case.
       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

If you did not use Something Else or even with Something Else install did not change the default from sda to sdf, you need to reinstall grub. If not booting, the Boot-Repair can repair it with its advanced mode.

      
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdf but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdf"  then just run:
sudo grub-install /dev/sdf
#If that returns any errors run:
sudo grub-install --recheck /dev/sdf
sudo update-grub

But the original install also stored the drive to reinstall into. On a major update, it may reinstall to that drive and default drive with older grub will not work. You can check which drive grub expects to reinstall into and change it if needed.

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 


 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Pete_Wilson on 2016-02-09
My thanks to oldfred and yancek for their quick and informative responses.  The issue, thanks to forum help is resolved.  I set it up so that I can choose to boot into the drive where ubuntu is installed from my BIOS.

---

