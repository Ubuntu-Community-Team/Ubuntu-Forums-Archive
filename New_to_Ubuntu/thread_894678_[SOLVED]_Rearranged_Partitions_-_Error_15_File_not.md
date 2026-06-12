---
title: "[SOLVED] Rearranged Partitions - Error 15: File not found"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by fadedhero on 2008-08-19
Hi, I am really new to linux, so please speak in absolute beginner talk. I have searched for other threads with this error, and have tried various fixes to no avail.

I have an ubuntu/vista dual boot. Recently, I rearranged and resized partitions on my hd. On reboot, I got the grub not found error. I booted into ubuntu with the live cd, found grub on (hd0,5) reinstalled grub. Rebooted. This time, grub started fine, but when i choose ubuntu, Error 15: File not found. Vista starts fine through grub, so my assumption is that even though grub is loading, it is telling the system to look for ubuntu in the wrong place.

Any help is greatly appreciated. If there is another thread that mentions my exact problem, please point me there. Thank you so much.

-Fadedhero

---

### Post by bobnutfield on 2008-08-19
Using the live cd, open a terminal and type:

> sudo fdisk -l

and then mount your hard drive partition with Ubuntu on and post the Ubuntu entry from /boot/grub/menu.lst

I think we can help you edit the menu.lst file to get Ubuntu back booting again.

---

### Post by fadedhero on 2008-08-19
Hi bobnutfield,
Thank you for the quick reply. Here is the response from the fdisk command:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15441544

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7180    57673318+   7  HPFS/NTFS
/dev/sda2            7181       18389    90036292+   f  W95 Ext'd (LBA)
/dev/sda3           18390       19457     8578710    7  HPFS/NTFS
/dev/sda5            7181       12924    46138648+   b  W95 FAT32
/dev/sda6           12925       18232    42636478+  83  Linux
/dev/sda7           18233       18389     1261071   82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131   de  Dell Utility
/dev/sdb2   *           6        3190    25583512+   c  W95 FAT32 (LBA)
/dev/sdb3            3191        3647     3670852+  db  CP/M / CTOS / ...

you mentioned mounting the partition with ubuntu on it. not sure how to mound something. would that be a cd type command? thanks.

---

### Post by bobnutfield on 2008-08-19
You mentioned that grub was installed to (hd0,5) but it comes up when your computer comes on?  If that is the case, then it is installed to the MBR.  In any case, when you have the live cd desktop open, go to Places and in the list should be your other partitions on your hard drive.  It will probably say something like "41GB Volume".  You just double click on that and it will automatically mount that partition and open a file browser.  The file you are looking for is /boot/grub/menu.lst (that is a small L not a one.)  In that file is the list of entries shown on the boot screen when grub comes up allowing you to choose your system to boot to.  What you need to post back is what the ubuntu entry is.  That is all that needs editing to get you booting back into Ubuntu.

---

### Post by fadedhero on 2008-08-19
I apologize for my inexperience. Here is the listing for ubuntu.

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fbbae82c-82b3-43b4-aeb7-62e6ab4a53ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fbbae82c-82b3-43b4-aeb7-62e6ab4a53ef ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

Thanks.

---

### Post by bobnutfield on 2008-08-19
> root (hd0,4)

OK, problem found.  Since linux is on /dev/sda6, the above should read (hd0,5).  So, you need to change all references to (hd0,4) to (hd0,5).  To do that, you need to open a text editor like this in a terminal:

> sudo gedit /media/disk/boot/grub/menu.lst

When it opens, just change the entry as indicated below:

> title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=fbbae82c-82b3-43b4-aeb7-62e6ab4a53ef ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

---

### Post by candtalan on 2008-08-19
> **fadedhero said:**
> Hi, I am really new to linux, so please speak in absolute beginner talk. I have searched for other threads with this error, and have tried various fixes to no avail.

I have an ubuntu/vista dual boot. Recently, I rearranged and resized partitions on my hd. On reboot, I got the grub not found error. I booted into ubuntu with the live cd, found grub on (hd0,5) reinstalled grub. Rebooted. This time, grub started fine, but when i choose ubuntu, Error 15: File not found. Vista starts fine through grub, so my assumption is that even though grub is loading, it is telling the system to look for ubuntu in the wrong place.

Any help is greatly appreciated. If there is another thread that mentions my exact problem, please point me there. Thank you so much.
-Fadedhero

As suggested in another message, it is possible that the content of the file
/boot/grub/menu.lst is pointing in menu.lst to an obsolete position of the file. 
As an example, my menu.lst includes the lines:

=====================================
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd1,0)
=====================================
 This means I am currently using ubuntu 7.10 and it (the system partition) is located in the second hard drive (hd1) inside its first partition ( ,0)

If your top line content in the file menu.lst is incorrect, you can edit it (take a backup copy first anyway) with a command some thing like
sudo /gedit/boot/grub/menu.lst although beware, this example is for when you are running in your installed ubuntu. From a live Cd with your installed partiotion mounted in say, /media/installed/
I think the command would be
sudo gedit /media/installed/boot/grub/menu.lst

My guess would be that your lines (assuming 7.10 and my versions.....) are likely to need to look like:
=====================================
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,5)
=====================================
hth

---

### Post by fadedhero on 2008-08-19
oOOoo, I see. Thanks. I am back into my ubuntu now. I did what you said and it worked perfectly.

---

### Post by bobnutfield on 2008-08-19
Glad we could help.  It might be good to remember that grub counts partitions starting with "0", so (hd0,5) is /dev/sda6, and that the menu.lst file has to be edited whenever you alter partitions.

---

