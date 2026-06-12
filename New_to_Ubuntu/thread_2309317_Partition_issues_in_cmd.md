---
title: "Partition issues in cmd"
date: 2016-01-09
forum: New to Ubuntu
---

### Post by blovoi on 2016-01-09
Hello everyone.  I am new to ubuntu and am looking to install it on my computer for the first time.  I am trying to partition half of my C drive to ubuntu though the cmd pannel. 
It's a 500 GB HD running a fresh install of Windows 10.  The only other partition is for the BIOS.  When I goto the properties in windows it shows 373 GB of free storage, but in the CMD pannel it only shows 51 GB available to partition.  Can someone help me understand this and try to resolve it?  


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
DISKPART> list disk


  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
* Disk 0    Online          465 GB    51 GB        *


DISKPART> select disk 0


Disk 0 is now the selected disk.


DISKPART> list volume


  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
  Volume 0     E                       DVD-ROM         0 B  No Media
  Volume 1     C   OS           NTFS   Partition    414 GB  Healthy    Boot
  Volume 2         SYSTEM       FAT32  Partition    300 MB  Healthy    System

---

### Post by yancek on 2016-01-09
The output you posted, the last three lines of your post, show a DVD drive, one 414GB windows partition and a 300MB partition which is most likely the EFI partition.  So you don't have any place on which to install Ubuntu.  You need to go into Disk Management on windows and shrink the windows partition to make as much room as you want for unallocated space on which you can install Ubuntu.  Make sure you boot or select to use UEFI when installing Ubuntu.  During the install, select the Something Else Installation Type option.  This will allow you to select the unallocated space to create and format partition with a Linux filesystem.  Read the Ubuntu documentation on this at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by deadflowr on 2016-01-09
I'd recommend loading Ubuntu's live cd, then selecting the option Try Ubuntu.
When it loads click on the windows key on the keyboard.
this will open the Ubuntu menu system.
The type : Gparted
Click on the icon the will show for gparted.
The when it opens, press the prntscrn button (usually to the right of the F keys)

The open firefox come to this thread and start a new post.
(you will need to either select reply to thread, or use the adv reply option)

In the new post click on the paperclip icon in the toolbar (above the post text area)
This is for attachments.
click on add files.
(The prtscn button takes screenshots of your desktop, so that will have put an image in the Pictures directory.)
Find that screenshot, and attach it.

I recommend this because a screenshot of gparted will probably give us a better understanding of the disk, over the way Diskpart currently is.
My two cents, at least

---

### Post by grahammechanical on 2016-01-09
Keep in mind that you are asking Ubuntu users to explain the differences between 2 different presentations of data in Microsoft's Windows.

465GB - 51GB = 414GB 

To me that looks like 51GB unallocated space in a 465GB disk. I would guess that the 373GB that is reported as free space by properties is actually free space inside the 414GB partition (Ltr C) that Windows 10 is installed in and that Windows 10 is taking up 41GB. A reasonable deduction?

500GB - 465GB = 35GB. There is 35GB of disk space that is not showing up. Not formatted? Not a partition? Or a hidden partition of some kind?

Regards

---

