---
title: "Installing Win7"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by Robert1305 on 2012-01-19
I use Ubuntu 11/10 and I think its the bees knees !!!!!!!!!

But I do need to use Win7 for a couple of things, what I would like to know do I just put my Win7 disk into my PC and just install it without having to do anything else. 

Regards Bob

---

### Post by nothingspecial on 2012-01-19
Have you thought about using it in a virtual machine?

How much ram do you have?

---

### Post by Jake Sweeney on 2012-01-19
I think it would be easier to install Windows 7 first and then Ubuntu afterwards if you want to dual boot.
If you want to just execute a program you could use Wine.
Or, if you have enough RAM, you can run a Virtual machine and install Windows 7 on that :D

---

### Post by Mark Phelps on 2012-01-19
> **Robert1305 said:**
> ...do I just put my Win7 disk into my PC and just install it without having to do anything else. 

Nope -- there is work to do because Windows can't understand Linux filesystems, so it can't see the existing partitions on your drive.

You need to boot into an Ubuntu desktop CD, choose Try Ubuntu, open Gnome Partition Editor, and shrink down your Ubuntu partition to make room.

After that, you should be able to reboot using the Win7 DVD and do an install to the free space.

---

