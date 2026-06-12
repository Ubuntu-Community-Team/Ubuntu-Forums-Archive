---
title: "Side by Side installation issues"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by nwrolla on 2012-04-13
Hi everyone, 
I am a new user to linux and Ubuntu. I have been using WUBI for the past few days trying to get acquainted with the system before doing a full install. I enjoyed WUBI except for the high CPU usage caused by the mount.ntfs program? I am not sure what causes it but it locked up the CPU fairly regularly for 5-10 seconds. I was trying to fully install Ubuntu 11.10 this morning with the USB drive.
I followed the instructions on the download page and when i booted Ubuntu from the drive and tried to click the installer on the homepage I was only had 2 options for installation instead of 3. The option to install side by side and adjust partitions with the slider is not available. (see image below, taken from Ubuntu tutorial) I was hoping to have a system that I could dual boot both OS's as I still need windows XP for a few programs from time to time. Any advice would be greatly appreciated I am running out of ideas on how to solve this. 
Main Questions - 
1.How can I install Unbuntu Side by Side with no option presented in the USB install menu? 
2. If a side by side installation is not possible, is there a fix for WUBI and the mount.ntfs eating up all of the CPU usage. 

System Specs- 
Windows XP 
CPU t7300 2ghz core duo 
4gb of RAM 
120gb Hard Drive 

Thanks again for the help, if there is anything I missed just let me know! 
[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/installation-type.jpg[/IMG]

---

### Post by Quackers on 2012-04-13
Welcome to UF and Ubuntu :-)

How many PRIMARY partitions does your system have currently?
Is the hard drive filled with partitions (even if those partitions are not full)?

Also you refer to XP but the installer refers to Windows 7. Which do you have?

---

### Post by nwrolla on 2012-04-13
Hi thanks for the reply. I believe I only have 1 primary partition. When I ran sudo fdisk -l It only showed the 120gb and the 2gb usb drive I booted from if I recall properly. Yes I am running XP I know it says windows 7 because the image was pasted from the Ubuntu Installation Walk-through.

---

### Post by Lemuriano on 2012-04-13
The reason is because you have more partitions than allow. To dual boot you would need to delete one of windows partitions using gparted from a live cd, but you have to be very careful so the windows install is not damage and do a backup of your data. 
I suggest you boot from live cd or usb, open gparted and post the partition you have.

---

### Post by Quackers on 2012-04-13
Ok, I see, thanks.
How big is your hard drive? Does the XP partition use it all?

---

### Post by nwrolla on 2012-04-13
> **Lemuriano said:**
> The reason is because you have more partitions than allow. To dual boot you would need to delete one of windows partitions using gparted from a live cd, but you have to be very careful so the windows install is not damage and do a backup of your data. 
I suggest you boot from live cd or usb, open gparted and post the partition you have.
Do I need a live cd or could I use the USB drive? Can I download and run gparted if I boot from the USB drive and use the terminal? Quackers I believe the XP partition would use the full drive? It is the only OS I have had since I last reformatted a year ago.

---

### Post by Quackers on 2012-04-13
If the XP partition uses the whole hard drive there is no space to install Ubuntu into. That would be why you are getting restricted options in the Ubuntu installer.
There must be unallocated space for Ubuntu to use.
You would therefore need to reduce the size of the XP partition so that some free space is left.
You should first defragment Windows and then shrink the size of the XP partition, if there is sufficient free space left.
You can then install Ubuntu into the new free space.

It is always good advice to backup anything you would not want to lose first!
Partition changing carries a (small) risk of disaster.

---

### Post by nwrolla on 2012-04-13
Thanks again Quackers, I defragmented already, and cleared 75-80gbs of free space in windows. With Gparted should I be able to create a new partition with the 70+ gbs of free space? Sorry for the simple questions.

---

### Post by Quackers on 2012-04-13
Sorry, I've been away.
If the XP partition takes up the whole drive you will need to resize that XP partition, thereby giving you some free space on the hard drive for Ubuntu to use.
That free space can then be used by Ubuntu. If the free space resides within the XP partition it's just unused space. Ubuntu can't use it because it's inside Windows' partition

In fact, if you want to check boot the Ubuntu live cd/usb and select "try ubuntu". This is always good practise so that you can make sure Ubuntu runs on your hardware.
Once the desktop is loaded open a terminal and run this ```
sudo fdisk -l
``` That's a small L not a 1.
Please post the output here.

---

### Post by nwrolla on 2012-04-13
Here are the Fdisk stats- First one is the main drive and second is the usb for the boot. 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   234420479   117210208+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2004 MB, 2004877312 bytes
247 heads, 62 sectors/track, 255 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb976784

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     3915775     1957856    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by Quackers on 2012-04-13
Thanks.
Yes, your XP partition is using the whole disc.
You need to resize (shrink) the XP partition - gparted on the live desktop can do this.
That will leave free space for Ubuntu to install into.

Make sure you have backups and after shrinking the XP partition reboot from the normal system to make sure Windows still boots.

You can then start again and install Ubuntu with all the options available, using the new free space.

---

### Post by nwrolla on 2012-04-13
I am in gparted in the live desktop and  I see the XP partition but I cannot adjust the size? it appears to be locked.  I am downloading the ISO to try to burn a disc and boot from the disk but I am at work right now.

---

### Post by Quackers on 2012-04-13
In gparted it should not be locked. Normally if a swap partition was present it may be necessary to right-click and select swapoff, but you don't have a swap partition. 
That is odd. Is there a key showing to the left of the XP partition?

Why are you downloading an iso? You are booted from a live cd now, yes?

---

### Post by nwrolla on 2012-04-13
There is no key locking it. I attached a screen shot file for you to see Hopefully this will help with solving the issue. Yes i am booted from a live cd (USB) I was downloading a Gparted ISO to burn to a cd and run that from the boot process instead of the USB. I was reading on this site looking for ideas. - 
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Quackers on 2012-04-13
Gparted is a handy cd to have.
Your XP partition is not locked but it has an exclamation mark next to it.
Right-click on the partition and select information and see what that says.
Also try right-clicking on it and selecting "check" and see what happens there.
I take it that Windows was booting ok.

EDIT It may be that your XP partition needs a chkdsk running.

---

### Post by nwrolla on 2012-04-13
Here is another screen shot of the exclamation point when i run the the check it fails out I attached a screenshot of that too. And yes windows boots up fine I will run a chkdsk

---

### Post by Quackers on 2012-04-13
I think a chkdsk would be wise.
If it finds errors keep running it until it stops reporting errors.
At that point gparted should be ok with it.

---

### Post by nwrolla on 2012-04-13
Running the Check disk, thanks for the help! I will update when I try to run gparted again.

---

### Post by Quackers on 2012-04-13
Ok, good luck :-)
It may take a while.
Let us know if that clears things up.

---

### Post by nwrolla on 2012-04-15
Worked perfect! once the disk check finished all was good for the installation.

---

### Post by Quackers on 2012-04-15
Excellent :-)
Thanks for the feedback.
Please mark the thread as solved using the Thread Tools near the top of this page.

---

