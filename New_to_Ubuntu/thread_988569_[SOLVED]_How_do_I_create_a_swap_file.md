---
title: "[SOLVED] How do I create a swap file"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Michaelg14 on 2008-11-20
My hard drive has too many partitions on it.  I would like to eliminate the swap partition and use a swap file instead.  I have created a swapfile in my home folder with mkswap but when I reboot and do swapon -s it shows no swap file or partition.  

If I do swapon followed by swapon -s I then get:

Filename				Type		Size	Used	Priority
/home/greybeard/swapfile                file		262136	0	-1

How do I tell Ubuntu to use the swap file automatically?

---

### Post by plucky on 2008-11-20
> How do I tell Ubuntu to use the swap file automatically? 

You will probably have to mount it in /etc/fstab so that it is always available.


See this [Swapfaq in Ubuntu Documentation](https://help.ubuntu.com/community/SwapFaq) link.


Good Luck

---

### Post by nhasian on 2008-11-20
although a hard disk can only have four primary partitions, one of them can be an Extended partition.  In the extended partition you can make logical paritions like one for your swap file.

---

