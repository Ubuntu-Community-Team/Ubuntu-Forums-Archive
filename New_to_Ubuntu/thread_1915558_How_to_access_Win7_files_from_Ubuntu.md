---
title: "How to access Win7 files from Ubuntu"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-01-26
I imagine this has been asked dozens of times before, but I have a dual boot system now with Windows 7 and Ubuntu. I would like to be able to access my Windows files via Ubuntu, but I have no idea how to do this.

I used Wubi to do the install, if that makes any difference.

---

### Post by bogan on 2012-01-26
Hi!, **Curtis6767,**

If you are using Ubuntu 11.10, when you open the Home folder there will be a SideBar listing 'Places' accessible.
 
The First batch are Devices and one, probably the first, will be: 'Boot'. 
That is your Windows 'C:' drive.
 
Click on it and it will be mounted and display all your Windows Drawers and files.

If you are using other versions it may be called something like: 125GB Filesystem. Try clicking it, the\display will be easily recognizable. An Icon will show on the Desktop and you can access it there. 

Similarly, if you have  more than one HDD with Windows files on it.Edit 2: The Disks and Partitions will be listed by their Windows names.

Edit1: I do not use Wubi, and know little about it, but I would be surprised if this is different. If it is, no doubt someone will correct me.

Chao!, **bogan.**

---

### Post by Morbius1 on 2012-01-26
>  I used Wubi to do the install, if that makes any difference.I don't use Wibi either but I believe your Windows files are automatically mounted at: **/host**

---

### Post by Curtis6767 on 2012-01-26
I found "BOOT", clicked on it but all I get are a bunch of files none of which have much in them but other small files.

I am using 11.10 and I'm a complete newb to linux and Ubuntu.

When I was using Ubuntu from the CD, before I installed it on its own partition, I was able to access the few files that I tried to access. 

from Ubuntu: "It'll work with your existing PC files, printers, cameras and MP3 players."

Okay, but how do I get to them?

Thanks

---

### Post by Curtis6767 on 2012-01-26
Found them.

Opened the Home Folder

Clicked on File System

This opened up a window with various files

one of the files was 'host.'

I clicked on that and that's where all the Win7 files were.

Thanks for the tip on 'host' otherwise I probably wouldn't have clicked on it.

---

### Post by mastablasta on 2012-01-27
in nautilus (ubuntu file manager) the NTFS (windows file system) is usually shown with it's volume label.

---

### Post by Mark Phelps on 2012-01-27
Reading your Windows files from inside Ubuntu should pose no problem, but be careful not to start updating them.

Win7 is very finicky about changes being made to its filesystem from "outside" -- which is what you're doing if you're changing files from Ubuntu.  This can result in filesystem corruption -- which may then render Win7 unbootable, and may prevent you from booting into Ubuntu as well (major downside of using Wubi).

---

