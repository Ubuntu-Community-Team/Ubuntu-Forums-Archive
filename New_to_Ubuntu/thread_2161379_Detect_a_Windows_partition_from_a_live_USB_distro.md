---
title: "Detect a Windows partition from a live USB distro"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by r3bol on 2013-07-10
Hi, I wanted to access a windows partition from one of my PCs using a live USB distro (Damn Small Linux in this case). I followed these steps...

1.    Open a terminal and type sudo su
2.    Type fdisk -l (note which partition contains the NTFS file system)
3.    Type mkdir /media/windows (This directory is where we will access the partition)
4.    Type mount /dev/hdx1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
5.    Type cd /media/windows (Moves us to the windows directory)
6.    Type ls to list the files on the NTFS partition

...but I'm stuck on step 2. It seems only the usb partition is available/visible. 

How can I 'see' the other windows ntfs partitions? 

Thanks.

---

### Post by sudodus on 2013-07-10
Maybe there is some feature of your ntfs partition or the whole partition table, that is not recognized by DSL. For example dynamic partitions or GPT. Try with a live Ubuntu 12.04.2 USB drive instead or some other current live system for example Knoppix.

Can you boot Windows? Could there be something wrong with the drive or Windows partition?

---

### Post by snowpine on 2013-07-10
I am not sure that DSL has that capability (it is old and not very well supported) but I'm quite certain you can easily access your Windows partition from an Ubuntu Live USB. :)

---

### Post by r3bol on 2013-07-10
Ok, thanks. I was just trying to download something quick to try a few things out, but I guess I should grab something a bit more modern.

---

### Post by sudodus on 2013-07-10
DSL is nice for very old hardware (and small RAM) but has its limits.

---

