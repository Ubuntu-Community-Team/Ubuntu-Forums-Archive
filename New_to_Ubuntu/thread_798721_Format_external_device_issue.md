---
title: "Format external device issue"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by logx on 2008-05-18
Hello everybody,

There are probably several hundred threads about this already but I've been the whole afternoon looking and I cannot find a solution.

I have an external MP3 (ZEN STONE) that I'm trying to format.

I can see it in Gparted under /dev/sdb but it doesn't have a partition yet (unallocated).

I tried giving a msdos one via gparted but the only thing it does is close gparted and when I come back everything is the same (still unallocated).

I tried to do it via console (fdsik dev/sdb) but nothing happens neither :s

Can somebody help me?:confused:

---

### Post by kwacka on 2008-05-18
If the volume is mounted gparted won't work.

If you are using nautilus, right-click on the desktop icon & unmount then try gparted.

fdisk -l will give the location of the file - just in case its not at /dev/sdb

---

### Post by logx on 2008-05-18
The problem is that I dont think the device is mounted because it doesn't appear in the Desktop.

I'm sure it is /dev/sdb since in gparted you have an option for more info and the name ZEN STONE appears on it

---

### Post by ChronoSphere on 2008-05-18
Try setting a new disklabel under the device menu. This will erase all partitions on the drive and create a new MBR.

---

### Post by logx on 2008-05-18
Weird thing, I formated the MP3 under OSX as msdos and now Ubuntu recognize it.

Why did it work on a MAC os and not in Ubuntu with Gparted?

What do you mean with the device menu?

---

