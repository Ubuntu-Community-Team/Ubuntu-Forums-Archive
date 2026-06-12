---
title: "Will My Flash Drive (NTFS) Support Ubuntu?"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by Ahmed_Musa on 2014-06-16
Hello, MY Superiors.

Please forgive me if this is the dumbest question ever but, I am a total beginner. Yes I have & am using Ubuntu on VBox but never plugged a flash drive in it. So, I've been thinking on totally moving on Linux (cause Windows is ****) and I'm studying up a little. So, after installing Ubuntu , IF I plug in my flash drive (its currently in NTFS file format 32gb) will it support it or Show up.. cause I really have important stuff in there and I don't feel like formatting it to ext3/4 ...
Also, if I HAVE TO format it I think I should do it after installing ubuntu , Right ?

I will be very Grateful even if u criticize of this being a dumb question and Thanks in Advance

---

### Post by rahul4557 on 2014-06-16
Ya..
**NTFS works on Ubuntu**
you will have to install the support package for NTFS
just type the following command in terminal

> sudo apt-get update
sudo apt-get install ntfs-3g

---

### Post by bcschmerker on 2014-06-16
The Ubuntu® Repositories have several Main packages for reading and writing volumes in the Microsoft® New Technology File System.  FUSE (Filesystem In Userspace) has a driver available with read-write capacity (packages: **libfuse2**, **fuse**, **ntfs-3g** and dependencies thereof).

---

### Post by Ahmed_Musa on 2014-06-16
[SIZE=5][FONT=comic sans ms]**[COLOR=#006400]Thanks Mate !!!!!  [/COLOR]**[/FONT][/SIZE]:D ... What can I ever do to repay u ..?

---

### Post by Impavidus on 2014-06-16
You don't even have to install anything, it's all there by default (at least on Xubuntu, I assume on Ubuntu too unless they decided to remove it for some strange reason). Just plug the drive in and it works.

---

