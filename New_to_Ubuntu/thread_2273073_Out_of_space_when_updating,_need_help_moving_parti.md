---
title: "Out of space when updating, need help moving partitions please"
date: 2015-04-10
forum: New to Ubuntu
---

### Post by mook2 on 2015-04-10
Running ubuntu 14.10.  When a software update becomes available, it tells me there is not enough space and to run sudo apt-get clean and empty the trash which I have. I could easily spare a few GB from sda3, but am not entirely sure which partition to move and how to do it without messing everything up.I looked through the forums for previous posts, but nothing seemed exactly applicable. Any help is greatly appreciated! :p Here is what i gparted shows:

[IMG]http://i.imgur.com/Qd1EyGQ.png[/IMG]

---

### Post by Bucky Ball on 2015-04-10
Welcome. Well, sda3 is full with 16 MiB remaining so unsure where you'd get any room from. Do you have an external device to back some stuff up to?

Two questions: Why are you using EXT2 for /boot and why are you using LVM? That can be problematic and unless you have a good reason and purpose for using it, you probably shouldn't bother. Make your life easier. ;)

If this is a fresh install I'd perhaps go again unless you really want to use LVM for something. How much data is sda3 supposed to have on it?

---

### Post by mook2 on 2015-04-10
Wait...now I'm completely confused. sda3 should be largely free. I have nowhere near that much crap saved, maybe 80GB max. I do use virtualbox to run windows so i can use corel paintshop, is that doing something ridiculous? It's not fresh, been using it for 6 months or so, but I really don't know the dif between boot and boot/efi? I also don't know what the lvm flag means ...

---

### Post by Bucky Ball on 2015-04-10
Before proceeding with the update, could you see if there is a kernel update included? That may use some of sda2 and it may be sda2 that it is complaining about. There appears to be a little room left on there, though. 

If the issue is related to LVM, I can't really help as am not familiar, sorry.

---

### Post by Impavidus on 2015-04-10
Looks like a classical case of a full /boot partition. I had a kernel update yesterday, so that's possible. Try removing some old kernels.```
sudo apt-get autoremove --purge
```usually does the trick.

sda3 isn't really full. Instead, it's completely used by a second partitioning layer (LVM) on top of the first, and gparted can't handle that situation.

---

### Post by mook2 on 2015-04-10
solved. the purge fixed it, 606 MB recovered, TY!!!!!

---

