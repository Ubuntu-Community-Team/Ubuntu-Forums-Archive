---
title: "A few questions"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by SCPChop on 2008-11-07
I just got Ubuntu and I heard you would be able to switch between using Ubuntu and WIndows in the beginning. I don't see that choice when I boot up my comp and I would like to use windows since I have a Zune. Also is it possible to bring files over from windows to Ubuntu like music, games, etc?

---

### Post by tompickles on 2008-11-07
How have you installed Ubuntu, or is it still running off the LiveCD? Also, if you ensure you don't delete your windows partition when you install, it will be added to your boot loader so you can boot both. alternitively, if you install with WUBI then you can use the windows boot loader and it will install without repartitioning. Also, if you install you can mount the windows partition to view files etc. Games you will likely as not need to install in an emulator such as WINE, else in a VM or.... just run native in Windows.

---

### Post by SCPChop on 2008-11-07
I ran the Live CD then installed. I dont remember what I did as I just clicked OK without changing anything.

---

### Post by tompickles on 2008-11-07
in the terminal, what does 

sudo fdisk -l

output. thats a lower case L not a 1.

---

### Post by DrMega on 2008-11-07
> **SCPChop said:**
> I ran the Live CD then installed. I dont remember what I did as I just clicked OK without changing anything.

Think back. You will have seen an option to either use entire disk, or partition it. What did you pick? If you don't get an option to boot into Windows, you might have chosen the 'entire disk' option, in which case Windows will have been blitzed.

---

### Post by tompickles on 2008-11-07
Yeh - sudo fdisk -l will list all the partitions on your hard disk so you can see what your hard disk has on it in terms of linux and windows partitions.

---

### Post by SCPChop on 2008-11-07
output is 
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0af20af2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9566    76838863+  83  Linux
/dev/sda2            9567        9729     1309297+   5  Extended
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris


I think I just deleted windows...lol...great. I dont have the disc for it either..freaking great.

---

### Post by tompickles on 2008-11-07
Seems that way. You have Ubuntu only on there I'm afraid. Sorry to hear you borked windows. Next time you install, double and tripple check the partitioning step.

---

### Post by SCPChop on 2008-11-07
lol should've been paying attention. Well time to reload all my songs from all my CD's. Anyone know if I can run Zune on Linux?

---

### Post by REDace0 on 2008-11-07
From what I gathered from [http://www.zune-online.com/mac-and-linux.html]("http://www.zune-online.com/mac-and-linux.html"), it works but is quite messy. However, based on the support I've seen from Rhythmbox for iPods, Ubuntu should automatically mount it as a USB Mass Storage device. I think Rhythmbox will also show it and let you sync to it inside Rhythmbox. However, there probably isn't support for any features of the Zune that go beyond playing music files.

Alternatively, go ahead and try to get some help for the methods listed on that site. Or you could (look up how to do this first, Windows does not install nicely next to Linux sometimes) reinstall Windows on its own partition. If you download the package gparted (GNOME Partition Editor), ```
sudo apt-get install gparted
```
You should have no problems shrinking your linux partitions to make room for Windows. Generally, Ubuntu has no problems mounting Windows partitions so that you can transfer files back and forth, however, going the other way around in Windows requires some extra software. I know it's out there, but I don't use it so I don't remember *where* exactly. Google it.

Hope that helps.

---

