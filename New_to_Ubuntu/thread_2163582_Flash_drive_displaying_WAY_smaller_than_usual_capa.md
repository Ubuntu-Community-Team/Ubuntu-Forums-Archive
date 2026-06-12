---
title: "Flash drive displaying WAY smaller than usual capacity"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by steamer360 on 2013-07-18
When I insert my Lexar 16 GB flash drive and go into the disk utility, it says that it is only 1/2 a MB! I also tried to go into GParted and it said the same thing. I tried formatting it again but that still didn't work.](*,) For some reason, my other computer (mac) does read the capacity as 16 GB. Has anyone ever encountered this problem or could help me with it? Thanks in advance!

---

### Post by nerdtron on 2013-07-18
On you mac, what is the filesystem of the flash drive? FAT32, NTFS?

---

### Post by steamer360 on 2013-07-18
> **nerdtron said:**
> On you mac, what is the filesystem of the flash drive? FAT32, NTFS?

I used FAT32, as I couldn't see an NTFS option.

---

### Post by steamer360 on 2013-07-18
Oops, I forget to mention that I tried reformatting my flash drive on my mac, and I used FAT32.

---

### Post by nerdtron on 2013-07-18
Can you try reformatting it in a windows system? Not sure though but if I remember correctly there are some issues regarding formatting flash drives in mac with the FAT32 option.

---

### Post by steamer360 on 2013-07-18
Sorry, no can-do. I don't have a windows computer, or easy access to one. Thanks for the suggestions though. Anything else that I could try?

---

### Post by nerdtron on 2013-07-18
Plug it in Linux.
In the terminal,
```
sudo fdisk -l
```

If should have an output like this:
```
Disk /dev/sda: 500.1 GB, 500106780160 bytes
```
That is my primary hard drive. If your flash drive is listed there and it is detected as 16GB, continue.
I'll assume your flash drive is /dev/sdb. Your going to format it again here.

```
sudo fdisk /dev/sdb
```
You'll enter the fdisk utility to edit the partitions.
Press d and hit enter to delete the partition.
Press w and hit enter to write changes.

Repeat:
```
sudo fdisk /dev/sdb
```
Press n and hit enter to create new partition.
For partition type, hit enter to accept the default.
For partition number, hit enter to accept the default.
Hit enter again to accept the default for First Sector.
Hit enter again to accept the default for Last Sector.
Press w and hit enter to write changes.

List the partitions:
```
 lsblk
```
You should see something like this:
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   1   7.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1   7.5G  0 part 
```

We need to format the /dev/sdb1 to FAT.
```
sudo mkfs.vfat /dev/sdb1
```

It should be done now.

---

### Post by steamer360 on 2013-07-18
Didn't even get past the first step. It came up with this: unable to read /dev/sdb: Invalid argument. Should I try reformatting it on my mac again?

---

### Post by nerdtron on 2013-07-18
O.o mind blown. You can try it again but I think it will still be the same.
Anyway, I'm not familiar with mac utilities but try searching for apps that can format flash drives using a Mac. Try to avoid using the default disk utility.

---

### Post by steamer360 on 2013-07-18
Okay, thanks for your help anyway. If I manage to get my flash drive properly recognized then your scripts will definitely come in handy.

---

### Post by 3rdalbum on 2013-07-19
Two possibilities:

1. Your flash drive has a little partition of read-only memory that contains some Windows software. That is what Ubuntu is seeing. If you eject that partition (NOT Safely Remove) you may find the real flash drive will appear on the desktop.

2. The flash drive is not genuine. Some that you buy cheaply on eBay are modified to report themselves as 16 gig capacity, but only have a small amount of flash memory and will fail to store more than a couple of gigs. It's a scam. However I think the first possibility is more likely.

---

### Post by carsten20101994 on 2013-07-19
Thanks for this thread... This thread solved my problem....
Thanks to all

---

### Post by steamer360 on 2013-07-19
I plugged in a different (not large enough size) flashrive into my linux machine and it worked fine, and automounted as well. The only difference is that the one that worked was usb 2.0, and the one that didn't work was usb 3.0. My linux computer only has usb 2.0 ports. My linux computer might not have been able to read usb 3.0, so it might be more of a hardware problem, not a software problem. Thanks for the help!

---

