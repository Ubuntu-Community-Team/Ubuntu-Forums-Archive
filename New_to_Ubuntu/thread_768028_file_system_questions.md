---
title: "file system questions"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by pmooney78 on 2008-04-26
Good evening!

I've recently transitioned to Xubuntu from Windows 2000. I have some general questions about the file system that I haven't been able to figure out from man pages, etc.

First: I'm dual-booting win2000 and Xubuntu Linux 7.10 (Xfce 4.4.1, kernel 2.6.22.14) on a Pentium III 550Mhz. I have two internal IDE hard drives, one an NTFS drive (3GB) with the win2000 installation and one a 6GB volume with a Linux swap partition and a the partition with Xubuntu 7 installed. I have an internal IDE CD-ROM drive and IDE DVD burner. I have two external USB hard drives, 80GB and 320GB, connected to USB 2.0 ports. 

I have a general understanding of how the file system is hooked together. I understand that the various "directories" I see under the root are actually pointers to physical devices or to parts of one of the hard drives, and I can find the various drives in their appropriate locations under /dev/s* and /media/. 

Here's what I'm wondering: Can I change the physical location corresponding to a certain virtual location? I'd like, for instance, to put /tmp on a larger drive, and perhaps put the /bin directory (and related directories) on a larger storage medium. Is there any reason not to move temporary files and programs to an external drive? (I realize that I may take a performance hit, but I'd like to try it and see whether it's noticeable.) And I'd like to make /dev/cdrom point to my DVD writer instead of my CD-ROM drive to fool my CD ripper ...

And, how can I partition my drives? I can find instructions on the Ubuntu forums, but they reference a tool (GParted?) that seems not to be available in the Xubuntu release. I know I've seen a graphical partitioning tool somewhere, but I can't find it anywhere...

Thanks in advance for any help!

---

### Post by melopsittacus on 2008-04-26
Hi pmooney!

I think you should search for a guide about /etc/fstab
That may tell you how to achieve your goals.

As for the partitioning you might try a console-based tool, like fdisk, if GParted is not available.

---

### Post by 3rdalbum on 2008-04-26
You can do that. Let's say you want /usr on a different hard disk. You would format the new hard disk as Ext3, copy your existing /usr onto the new hard disk, and edit /etc/fstab to tell it to mount the new hard disk to the location "/usr". Before rebooting, delete the current /usr from your old hard disk.

---

### Post by zvacet on 2008-04-26
For partition use [Gparted live Cd.]("http://gparted.sourceforge.net/")

---

### Post by pmooney78 on 2008-04-26
... and I discover I can install gparted through the Synaptec package manager, too. Thank you very much!

---

