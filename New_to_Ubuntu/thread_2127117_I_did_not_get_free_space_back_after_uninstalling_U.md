---
title: "I did not get free space back after uninstalling Ubuntu 12.10 via wubi"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by nershin on 2013-03-19
Hello!

I installed Ubuntu 12.10 via wubi. Because of some problems with the wifi connection I chose to uninstall it. I started wubi again and it said that I have to uninstall ubuntu before installing it again. So I agreed to uninstall ubuntu without installing a new version. However, although ubuntu is gone (or so it seems, I cannot access it anymore), I now have 4GB less free space available on my hard disk. I started the disk management, and there is no ubuntu partition. I wonder where the 4GB have gone, I would like to remove it completely. I did not install anything else in the meantime. 

I use a Thinkpad e420s with Windows 7 Pro OEM. 

Thanks a lot.

---

### Post by Cheesemill on 2013-03-19
Wubi installations live in the C:\ubuntu folder unless you specified a differnet drive during installation.

If there is no data you need from the Ubuntu installation then you can just delete this folder, although it should have been done for you when you uninstalled Ubuntu.

---

### Post by nershin on 2013-03-19
The folder does not exist anymore, so there is nothing that I can delete. 

The  disk manager says that my hard disk has a capacity of 119,24GB.  However, the listed size is 128GB. Is this difference of 9GB normal? As  far as I can see, this is the only place where the 4GB might have been  lost.

Is it possible that Windows installs updates of the size of  4GB within a few hours? I have to say that my notebook is brand new.

---

### Post by Cheesemill on 2013-03-19
You're getting caught out by the different way in which people measure GB.

Hard drive manufacturers use the measurement 1GB = 1000 x 1000 x 1000 Bytes whereas computers use the measurement 1GB = 1024 x 1024 x 1024 Bytes. If you do the maths then what drive manufacturers call 1GB is actually 0.93GB.

The actual size of your hard drive is 128GB x 0.93 = 119.2GB which is what is being reported, you haven't lost any space.

[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by sudodus on 2013-03-19
> **nershin said:**
> The folder does not exist anymore, so there is nothing that I can delete. 

The  disk manager says that my hard disk has a capacity of 119,24GB.  However, the listed size is 128GB. Is this difference of 9GB normal? As  far as I can see, this is the only place where the 4GB might have been  lost.

Is it possible that Windows installs updates of the size of  4GB within a few hours? I have to say that my notebook is brand new.

It might be different ways of specifying Gb:

either 1 GB =10^9 B or 1 GB = 1024*1024*1024 B (alias Gibibytes)

119.24*1.024*1.024*1.024=128

---

