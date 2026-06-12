---
title: "Extend Ubuntu partition to left"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by KeremE on 2013-10-27
Hi, 

I'm trying to shrink my Windows partition in order to extend my Ubuntu partition using GParted, but it seems as if I'm doing something wrong. In GParted, running off of an Ubuntu LiveCD (actually flash drive), I have the Windows partition to the left of my Ubuntu partition, and I have successfully shrunk it. However, I can't find any option to extend the Ubuntu partition to the left to use the unallocated space. Based on what I've read, I need to move my Ubuntu partition to the left first, before extending, but it seems to involve creating a new partition and copying my Ubuntu partition over. However, I don't think I can do that because I already have 4 partitions on my HD. 

I think I must be missing something, as I expected this to be a simple task. Any suggestions?

Thanks!

---

### Post by Baldrick_NZ on 2013-10-28
Any chance you could post a screen grab of the gparted window so we can better see the way it is currently, then help from there? You kinda want to know for sure when partitioning drives.

---

### Post by Impavidus on 2013-10-28
I think your Ubuntu partition is a logical partition inside an extended partition, in which case you'd have to expand the extended partition first. You can simply expand partitions to the left. If you have a swap partition inside that extended partition too, switch it off first. But show us a screenshot of that gparted window first, so that we can be really sure.

As a sidenote, shrinking your Win7 partition using gparted may or may not work. It sometimes seems to damage the Windows partition. To be sure, we usually recommend using a Windows tool to shrink Win7 partitions.

---

