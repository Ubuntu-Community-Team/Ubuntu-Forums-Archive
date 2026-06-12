---
title: "Getting rid of Windows 7 loader partition"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by vmsda on 2011-12-23
At present, my pc sports the following partitions:

sda1 - Windows 7 loader partition
sda2 - Windows 7
sda3 - Ubuntu 10.04
sda4 - Reserved for coming install of Lubuntu

I created sda3 and sda4 with the help of my trusted and tried SystemRescue CD.

I should like to get rid of W7 loader partition and boot W7 from sda2 directly. Can I just use SystemRescue to turn sda1 into a Swap partition to be used by either Ubuntu system?

Thank you in advance for your help.

---

### Post by saneearth on 2011-12-23
Likely Grub is loaded on sda1. You can't really get rid of this and use if for swap without loosing your ability to boot at all. If however you happened to install on sda3, then you can do anything you want with sda1 including reformatting it and making it a swap partition.

Gregg aka saneearth

---

### Post by BC59 on 2011-12-23
@saneearth most propably is installed on sda1

@vmsda Run this and post the result

```
sudo parted /dev/sda print
```
```
sudo fdisk -l          #(it's a lower case L)
```

---

### Post by vmsda on 2011-12-23
> **BC59 said:**
> ... @vmsda Run this and post the result
```
sudo parted /dev/sda print
```
```
sudo fdisk -l          #(it's a lower case L)
```

Here are the results:
```
Model: ATA TOSHIBA MK4058GS (scsi)
Disk /dev/sda: 400GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         hidden
 2      106MB   133GB  133GB  primary  ntfs         boot
 3      133GB   273GB  141GB  primary  ext3
 4      273GB   400GB  127GB  primary  ext3

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74371ff3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   17  Hidden HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13       16157   129677678+   7  HPFS/NTFS
/dev/sda3           16158       33244   137251327+  83  Linux
/dev/sda4           33245       48641   123676402+  83  Linux
```

Commment: I owe you an explanation as to the flags of sda1 and sda2. With SystemRescue CD I first took the Boot flag off sda1 and set it on sda2, ran update-grub; then I hid sda1. Windows still boots ok, but I am not sure from which partition :)

I do not mind eliminating sda1, rearranging the partitions in order to have a swap partitions further down the list, with SystemRescue that is no problem. With one proviso: even though I very rarely boot Windows, I want to keep it just in case.

Thank you again for your comments.

---

### Post by Mark Phelps on 2011-12-23
The safest way to rid yourself of the need of the first partition to boot Win7 is to do the following:
1) Download and install EasyBCD from NeoSmart Technologies into Win7
2) Run EasyBCD
3) Click on the BCD Bacup/Repair button
4) Click on the Change boot drive button
5) Select the partition containing the Win7 OS
6) Exit out of EasyBCD

The Win7 boot loader files have now been installed to the Win7 OS partition -- so you no longer need the first partition for booting Win7.

---

### Post by garyed on 2011-12-23
The easiest thing might be just to change sda4 to an extended partition if there's nothing on it now. Then you won't have to worry about the four primary partition limit in the future. Leaving that small sda1 partition would probably never be a problem.

---

### Post by BC59 on 2011-12-23
If you are confused, there is always an easy solution.
Backup all your personal data.
Then boot from a Live CD and delete all the partitions of the Hard drive.
After that install Ubuntu from the scratch.
It's the easiest solution and the most effective.

---

