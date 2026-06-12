---
title: "Mount a virtual drive, what is the optimal protocol?"
date: 2007-09-14
forum: Programming Talk
---

### Post by mohamedafattah on 2007-09-14
I am trying to write a program that keeps track of files and folders (versions and so). In order for this program to have the most functionality, I thought about making a virtually mountable drive on Linux. I thought about an NFS server, but seems complicated (I am not used to RPC programming in C, and there are a few references). I also thought about an FTP server, but seems not mountable in Linux. Anyway, I think both of them need to be done carefully to stay away from security holes. So, I decided to keep away from Network File Systems.

I am asking if there is a way to make a virtual drive program in whatever language and protocol? Any ideas, links, or references is appreciated.

The point here is that my program should be serving the kernel with virtual files when it requests it.

---

### Post by CptPicard on 2007-09-14
I am not really sure what you need here, but the so-called "[loop device]("http://en.wikipedia.org/wiki/Loop_device")" can be used to mount filesystems that are stored in a file. You might also consider a [ramdisk]("http://www.vanemery.com/Linux/Ramdisk/ramdisk.html").

If you're really into kernel hacking, you might want to write a genuine [virtual filesystem driver]("http://lwn.net/Articles/13325/").. :)

---

### Post by mohamedafattah on 2007-09-14
Thanks a lot.

That was really fast and useful. The third link was the thing I targeted.

---

