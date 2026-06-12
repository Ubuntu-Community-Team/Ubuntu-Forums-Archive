---
title: "Ubuntu 12.10 usb transfer issue"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by eth1cal on 2013-03-29
I have been searching and still have not found a fix for this usb slow transfer issue. When transfering a file lets say 4 gb or more it starts off fast, slows down to like 21 mbs and then will soon freeze and lock everything up to where i have to restart. Does anyone know of a fix for this issue.. 

thanks

---

### Post by arpanaut on 2013-03-29
How big a drive?
What file system?

If fat32 it does not support file size of 4 Gb or larger

---

### Post by slickymaster on 2013-03-29
How is your USB formatted?
The reason I ask is because there's a limit of file size admissible to copy according to the file system. With FAT32, the maximum file size is 4.3GB.

---

### Post by eth1cal on 2013-03-29
It is in NTFS. I have transfered alot of big files to it when I had windows. What is happening is around 2.2 to 3 gigs it sounds like my cpu fan kicks on really high and get really loud and it just freezes I can't move the mouse anything. This never happened on this laptop when it has windows on it. I was thinking something must be going on somewhere in 12.10 I don't know about hehe. I am very new to linux

---

### Post by AndyOpie150 on 2013-03-29
What there saying is true. NTFS, FAT16, FAT32 all have limitations on data transfer size. Mine would lock up as well when I tried to transfer to much at one time.
Try either to split up the data transfer to chunks of less than 500MB, or reformat the USB drive to ext.2, 3, or 4. 
If you need to transfer data back to a Windows OS it might not see the drive if ext.2, 3, or 4. 

I personally just broke up the data transfer to smaller chunks.

---

### Post by 3rdalbum on 2013-03-30
NTFS writing is heavily CPU-bound on Linux.

What this means is that write speed to an NTFS hard disk will depend on how powerful your CPU is, and while writing to NTFS your CPU will be running at full steam.

This is okay, it's not dangerous and won't damage your hardware.

But it sounds like your CPU is gradually overheating. You might have dust in your CPU cooler, or simply not be able to dissipate the heat from your CPU running at 100%; this is a bad CPU cooler/fan if it can't do that. When the CPU starts overheating, it purposely runs at a lower speed to try and generate less heat (this explains the copying slowing down), and eventually if the heat keeps rising the CPU will automatically shut off to prevent damage. This immediately halts the computer.

Best thing to do is check your CPU cooler or have an experienced computer hardware person take it off and check it or replace it with something better. Your second-best option is to format your USB disk to ext4 or fat32. The latter cannot store files greater than 4 GiB.

---

