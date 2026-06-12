---
title: "Vista/Ubuntu7.10 - can't fix grub error 17"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Alexandre76 on 2008-10-13
Good Morning everyone,

I've just installed Ubuntu 7.10 on my system which has 3 hard drives. I've emptied one of them for dedicating it to Ubuntu, installed but I got the error 17 at first boot attempt.

I've found this thread which describes exactly my situation, but I cannot apply the solution:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

When I type root (sdc1,0) I get the error message Error 23: Error while parsing number (See mbwardle's posts, step 10)

Any help would be greatly appreciated.

Regards, Alexandre

---

### Post by Orange_and_Green on 2008-10-13
Hello Alexandre,

> **Alexandre76 said:**
> When I type root (sdc1,0) I get the error message Error 23: Error while parsing number

that should be ```
root (hd2,0)
```

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> Hello Alexandre,



that should be ```
root (hd2,0)
```

grub> root (hd2,0)

Error 21: Selected disk does not exist

My discs are shown like this in Gparted:

/dev/sda1 (Windows)
/dev/sdb1 (DATA)
/dev/sdc1 (Ubuntu)

---

### Post by Orange_and_Green on 2008-10-13
/dev/sda, /dev/sdb, /dev/sdc are the disk drives as the Linux file system sees them. /dev/sda1, /dev/sda2, /dev/sdb1 etc. Are the partitions on said drives, again as Linux file system sees them.

However, GRUB does not work with those. Rather, it calls the disks hd0, hd1, hd2 and so on, in the order that BIOS sets them up for boot. The digit after the comma specifies the n-th partition on that disk (so, for example, (hd1,0) would indicate the first partition of the second disk in boot order, as numbering starts with zero).

Have you checked the boot order in your BIOS and made sure that the disk you want is actually recognized, and the third one in boot order? You might want to try, for instance, making the Ubuntu disk first one in boot order and do

```
root (hd0,0)
```

from the GRUB prompt.

Good luck:KS

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> /dev/sda, /dev/sdb, /dev/sdc are the disk drives as the Linux file system sees them. /dev/sda1, /dev/sda2, /dev/sdb1 etc. Are the partitions on said drives, again as Linux file system sees them.

However, GRUB does not work with those. Rather, it calls the disks hd0, hd1, hd2 and so on, in the order that BIOS sets them up for boot. The digit after the comma specifies the n-th partition on that disk (so, for example, (hd1,0) would indicate the first partition of the second disk in boot order, as numbering starts with zero).

Have you checked the boot order in your BIOS and made sure that the disk you want is actually recognized, and the third one in boot order? You might want to try, for instance, making the Ubuntu disk first one in boot order and do

```
root (hd0,0)
```

from the GRUB prompt.

Good luck:KS

Ok, I've managed to type the commands from steps 10 and 11...

grub> geometry (hd2)
drive 0x82: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sdc
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> geometry (hd1)
drive 0x81: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> root (hd2,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd2,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub> 

I am not sure how I can edit menu.lst

---

### Post by Orange_and_Green on 2008-10-13
Good, congratulations!

> **Alexandre76 said:**
> I am not sure how I can edit menu.lst

That would depend, of course, on which drive is the one GRUB is installed to. Editing menu.lst on hd2 would not do any good unless that drive is moved to first in boot order (providing GRUB is installed to that drive).

Could you please boot from a live CD and post the output of
```
sudo fdisk -l
```?

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> Good, congratulations!



That would depend, of course, on which drive is the one GRUB is installed to. Editing menu.lst on hd2 would not do any good unless that drive is moved to first in boot order (providing GRUB is installed to that drive).

Could you please boot from a live CD and post the output of
```
sudo fdisk -l
```?

I mean I know how to edit the file, but not how to save it as it tells me I don't have the authorization for saving the modification..

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
6 heads, 4 sectors/track, 26047602 cylinders
Units = cylinders of 24 * 512 = 12288 bytes
Disk identifier: 0xcf2ecf2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          86    26047403   312567808    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdef6370c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ddf22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       37781   303475851   83  Linux
/dev/sdc2           37782       38913     9092790    5  Extended
/dev/sdc5           37782       38913     9092758+  82  Linux swap / Solaris

Disk /dev/sdh: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1         123      987104    7  HPFS/NTFS
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> Good, congratulations!



That would depend, of course, on which drive is the one GRUB is installed to. Editing menu.lst on hd2 would not do any good unless that drive is moved to first in boot order (providing GRUB is installed to that drive).

Could you please boot from a live CD and post the output of
```
sudo fdisk -l
```?

FYI, here is my menu.lst file

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99251a8e-36a2-4a24-a9ae-4d01d1370993 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99251a8e-36a2-4a24-a9ae-4d01d1370993 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Orange_and_Green on 2008-10-13
Very good :)

type ```
gksu gedit
``` to open a text editor with root privileges so it will let you save the file. Select "open", navigate to the file, open, write your modifications and save.

Alternate method:

```
gksu nautilus
```

This will open up a browser window with root privileges. Navigate to the menu.lst file, double click, modify and save.

Good luck :KS

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> Very good :)

type ```
gksu gedit
``` to open a text editor with root privileges so it will let you save the file. Select "open", navigate to the file, open, write your modifications and save.

Alternate method:

```
gksu nautilus
```

This will open up a browser window with root privileges. Navigate to the menu.lst file, double click, modify and save.

Good luck :KS

Thanks for the tip :) I am a little bit confused here... :confused: Shall I modify the menu.lst file by replacing hd2 with hd1 ?

---

### Post by Orange_and_Green on 2008-10-13
I think we need to clarify a few things first too... here goes:

1) Your computer boots to a Grub shell, which means the mbr of the first hard drive in BIOS boot priority points to a GRUB installation

2)However, for some reason, it doesn't find a menu file.

3)The command root(hd2, 0) run from the GRUB shell finds the Ubuntu disk

Is this correct so far?

If it is, then the best thing to do IMHO would be to leave hd2 in the menu.lst, and reinstall grub by specifying the location of the menu.lst file to it. The command to do this is

```
sudo grub-install --root-directory=ROOTDIR /dev/sda
```

where ROOTDIR is the GRANDPARENT directory of the menu.lst (if the menu.lst file is in /wherever/boot/grub/menu.lst, then the root directory is /wherever).

If you can tell me the full path of the menu.lst file (right-click->Properties, "Location"), I can tell you the exact command you need to issue. Good luck :KS

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> Very good :)

type ```
gksu gedit
``` to open a text editor with root privileges so it will let you save the file. Select "open", navigate to the file, open, write your modifications and save.

Alternate method:

```
gksu nautilus
```

This will open up a browser window with root privileges. Navigate to the menu.lst file, double click, modify and save.

Good luck :KS

BTW, many thanks for your answers :0 It opens the text editor, but I cannot browse to the file... it seems to be stuck in a place, and i cannot choose where I want to browse... :(

---

### Post by Orange_and_Green on 2008-10-13
> **Alexandre76 said:**
> BTW, many thanks for your answers :0 It opens the text editor, but I cannot browse to the file... it seems to be stuck in a place, and i cannot choose where I want to browse... :(

Please post the file's location as I suggested in my previous post and I will teach you how to reach it... You will learn how the Linux file system is organised this way which is obviously a tremendous help for the future as well ;)

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> I think we need to clarify a few things first too... here goes:

1) Your computer boots to a Grub shell, which means the mbr of the first hard drive in BIOS boot priority points to a GRUB installation

2)However, for some reason, it doesn't find a menu file.

3)The command root(hd2, 0) run from the GRUB shell finds the Ubuntu disk

Is this correct so far?

If it is, then the best thing to do IMHO would be to leave hd2 in the menu.lst, and reinstall grub by specifying the location of the menu.lst file to it. The command to do this is

```
sudo grub-install --root-directory=ROOTDIR /dev/sda
```

where ROOTDIR is the GRANDPARENT directory of the menu.lst (if the menu.lst file is in /wherever/boot/grub/menu.lst, then the root directory is /wherever).

If you can tell me the full path of the menu.lst file (right-click->Properties, "Location"), I can tell you the exact command you need to issue. Good luck :KS

The windows's title says menu.lst (/media/disk/boot/grub)

---

### Post by Orange_and_Green on 2008-10-13
> **Alexandre76 said:**
> The windows's title says menu.lst (/media/disk/boot/grub)

Excellent. Try

```
sudo grub-install --root-directory=/media/disk/ /dev/sda
```

Wait for it to finish (it may take a minute or so) then reboot. let me know how it went.

Good luck :KS

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> Excellent. Try

```
sudo grub-install --root-directory=/media/disk/ /dev/sda
```

Wait for it to finish (it may take a minute or so) then reboot. let me know how it went.

Good luck :KS

Thanks, I will reboot now and update the post asap :)

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/disk/ /dev/sda
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /media/disk//boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/media/disk//boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /media/disk//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdc
(hd2)   /dev/sdb
ubuntu@ubuntu:~$

---

### Post by Orange_and_Green on 2008-10-13
Keepin my fingers crossed... You should get at least a GRUB menu with the entries for the various OSes you have by now.

If you still can't boot, then do

```
gksu gedit /media/disk/boot/grub/menu.lst
```

This will allow you to edit menu.lst AND save it.

You might then try replacing hd2 with hd1.

Good luck :KS

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> Keepin my fingers crossed... You should get at least a GRUB menu with the entries for the various OSes you have by now.

If you still can't boot, then do

```
gksu gedit /media/disk/boot/grub/menu.lst
```

This will allow you to edit menu.lst AND save it.

You might then try replacing hd2 with hd1.

Good luck :KS

Thanks a millions! I am posting this from Windows Vista, as I couldn't start to Ubuntu due to an error 17 again, but with an error code this time: couldn't mount the selected partition.

I mark this threat as resolved, and will look through the forums for the other error... and hopefully I can soon stop using Vista !!! :)

---

### Post by Orange_and_Green on 2008-10-13
Good luck!! I really feel for you and I too wish you can stop using vista for good...

Does the same error pop up with hd1 instead of hd2 as well?

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> Good luck!! I really feel for you and I too wish you can stop using vista for good...

Does the same error pop up with hd1 instead of hd2 as well?

I didn't have this error before, just error 17 without any message such as "cannot mount the selected partition".

---

### Post by Orange_and_Green on 2008-10-13
> **Alexandre76 said:**
> I didn't have this error before, just error 17 without any message such as "cannot mount the selected partition".

This is precisely why I'm asking. Now that (apparently) the menu.lst file is correctly being read by GRUB, we need to find out what device identifier (hd1, hd2, etc.) points to Ubuntu.

---

### Post by Alexandre76 on 2008-10-13
> **Orange_and_Green said:**
> This is precisely why I'm asking. Now that (apparently) the menu.lst file is correctly being read by GRUB, we need to find out what device identifier (hd1, hd2, etc.) points to Ubuntu.

It's HD1, i've pressed the keystroke 'e' when booting, and modified the line to make is boot from hd1

I'll still be using Vista are there are too many programs not compatible, but it's a good start :)

Alexandre

---

### Post by Orange_and_Green on 2008-10-13
Glad you had a good start, and very glad we finally got things working.

Please feel free to use whatever suits your needs most, obviously. But if you generally like linux and the reason you cannot "cross the line" is simply windows programs you need to use, I'd just like to let you know that there are ways to make them work in Linux as well (Linux ports, open-source equivalents, wine, virtual machines...)

If you like, you can always post a list of windows programs you'd like to use and we will tell you if there is a way to do the same things in Ubuntu as well (most often there is ;))

Thank you for posting, have a nice day :KS

---

