---
title: "HDD not visible/not partitioned?"
date: 2016-09-19
forum: New to Ubuntu
---

### Post by maykal on 2016-09-19
Hello,

I'm new to Ubuntu and Linux. Bought a new PC with it two days ago and have been trying to get to understand how it all works. No real IT knowledge either so all a bit tricky. I've just upgraded to 16.04.

The PC system I bought has a 1TB HDD. However, when I try to transfer files to the desktop, it almost immediately says that it's run out of memory, even though I only have the system installed and nothing else (except a couple of apps - Chrome, Google Earth, etc). I opened System Monitor and it tells me:

/dev/sda2/ type: ext4 Total: 7.7GB Available: 961MB Used: 6.4GB (86%)

So I guess that somehow it's not using the rest of the space, just this partition, so when I try to copy across my files (work docs, pics, videos, etc) into folders on the desktop, it just tells me there is no room. Is there some way I can attribute more space? Can I dedicate a separate partition for personal docs/file/etc? Really at sea here.

Cheers.

---

### Post by maykal on 2016-09-19
Update - found Gparted, found all the unallocated space, and created a new partition. Any layman's instructions on how to set this as the home partition?

---

### Post by Impavidus on 2016-09-19
So you bought a computer with Ubuntu preinstalled, although not the most recent version, with a strange partitioning. Best to see the details. We'll use the terminal, just because it makes it easier to communicate via the forum. Open a terminal (hit ctrl+alt+t) and run these two commands:```
df -h
sudo parted -l
```Note: the second command will ask you for your password. Nothing will show up when you type it, so just type and hit enter.

These commands will show the partitions on your hard drive, where they are mounted and how much space is available. Post the output here. Use code tags in your reply.


Update: Some instructions on moving your home directory to a separate partition: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by maykal on 2016-09-19
Hello and thanks,

Yes, it was preinstalled with 14.04 and now it's running 16.04. Here are the two items:

df -h:

```
Filesystem      Size  Used Avail Use% Mounted onudev            2,9G     0  2,9G   0% /dev
tmpfs           591M  8,9M  582M   2% /run
/dev/sda2       7,3G  6,7G  221M  97% /
tmpfs           2,9G  6,1M  2,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           2,9G     0  2,9G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           591M  4,0K  591M   1% /run/user/112
tmpfs           591M   56K  591M   1% /run/user/1000
```

sudo parted -l:

```
Model: ATA WDC WD10EZEX-00W (scsi)Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system     Flags
 1      1049kB  4096MB  4095MB  primary  linux-swap(v1)
 2      4096MB  12,1GB  8000MB  primary  ext4            boot
 3      12,1GB  851GB   839GB   primary  ext4

```

The 3rd partition (851GB) is the one I've created and would like to use for storage of folders and files and stuff. Sorry if I'm lacking a bit in terminology and know-how, the last time I did anything vaguely programmingish on a PC was on an Acorn Electron!

---

### Post by Impavidus on 2016-09-19
Your root partitions is only 7.3 GB, which is too small for comfort. You can't change the root partition of a running system, so you'll have to boot from a live disk and use gparted from there to make it larger. 15 GB is the smallest that works well, but you're not really tight on disk space so you can make it about 25 GB.

The link I provided in my previous post tells you how to move your /home directory to the new partition. Read it and ask questions here, if any.

When you boot from a live disk you could also simply do a fresh install of Ubuntu 16.04, but you'll have to pay attention to some details like proprietary drivers, partitioning and reinstalled applications, so maybe you don't want to do that now.

---

### Post by maykal on 2016-09-19
All getting a bit complicated for a non-tech person like me. Does it get any easier with time or do I basically have to learn to be a programmer to print a couple of documents for work? :)

I started working through the link you sent me, but when I enter the command for duplicating the fstab, it asks for my password, I enter it, and then it just comes back with the command cursor thing. Has it saved the duplicate somewhere or should it appear in the terminal?

---

### Post by maykal on 2016-09-19
Ok, think I've managed to get through the 'home' part, have 800GB in home now and can transfer all my docs quite happily. Thanks for the link for that!

I'll start looking into the live disk think now. I guess that's something I have to make, on a flash stick? I didn't get a Ubuntu disk with the PC when I bought it (as far as I can see).

---

### Post by oldfred on 2016-09-19
Did you expand / (root) before creating the /home?
I normally have a 25GB / partition, and use about 13GB with all data in a separate /mnt/data partition.
If you have kept root at 8GB, you will constantly have to houseclean, which you should do anyway, but may not be able to add many additional software programs.

Best to resize before you have lots of data in /home.

---

### Post by Impavidus on 2016-09-19
You can download a .iso file from the official Ubuntu website and make a bootable usb drive. One of the best ways to do so is the tool mkusb: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

The live usb is a great tool to have. You won't need it often, but it's useful when changing partitions or to fix the system if it's broken.

---

### Post by maykal on 2016-09-20
Good morning,

When I made the home partition, I didn't allocate all of the remaining HDD space to it, I kept some by just in case so I still have 140GB unallocated. I had already noticed that I had to keep emptying the trash to run some operations so I guess my next task is to do as you both suggest and make it 25GB so I can start adding some software. And good layman's walkthrough links for expanding the partition?

Thanks gents and have a lovely day.

---

### Post by Impavidus on 2016-09-20
You kept some unpartitioned space after creating the home partition, but you left it on the right side of the home partition. To enlarge the root partition, you need the unallocated space on the left of the home partition.

Create a live usb and boot from it. You may have to change the boot order in the bios. With a bit of luck it will start without a problem. Sometimes, depending on your hardware, you get a black screen. In that case, hit a key when you see the screen with a keyboard+human symbol and select the boot option nomodeset. Select "try ubuntu without installing".

Once you have your live session running, open gparted. You used it before. Use it to move the left edge of your home partition to the right to get some free space and then to expand the root partition. It may take a while.

---

### Post by maykal on 2016-09-23
Thanks, I'll give it a go when I've got a bit of time!

---

