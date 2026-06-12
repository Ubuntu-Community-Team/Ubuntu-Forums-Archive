---
title: "Data is being saved in /dev/loop0 and not where it should - Ubuntu 12.04"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by I am desperate on 2012-06-30
I have one small partition for Windows 7 and and a bigger one for Ubuntu 12.04.

I  just installed Ubuntu and the disc space should be completly free and  available. It is supposed to be 125G big, however it seems the all the  data I copy onto the computer goes to the wrong place. As said it was  supposed to be saved in the patition which is 125G, instead everything  is saved in /dev/loop0. I assume /dev/loop0 should be for the system, and  nothing else.


****** screenshot of the problem: [http://imgur.com/7p1IF](http://imgur.com/7p1IF)

What am I doing wrong? Is this why everything is so slow? How can I fix this?

---

### Post by mapes12 on 2012-06-30
You may want to have a look at this:-

[http://en.wikipedia.org/wiki/Loop_device](http://en.wikipedia.org/wiki/Loop_device)

It appears that your install hasn't gone as planned. I've not used windoze in ages but from reading posts on here it has its own partitioning tool that has to be used to preserve the integrity of Win 7 i.e. the likes of GParted should not be used. 

I guess if you can call up the Win 7 partitioner then you need to recreate the clean space for Ubu to site along side win 7 then attempt the dual boot again. If Grub needs to be reconfigured after the install then take a look at this handy utility:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mcduck on 2012-06-30
Did you install Ubuntu using the Wubi installer (from inside Windows)?

In that case Ubuntu is installed inside a loopmounted filesystem located in a file in the Widnows partition, instead of using a separate partition of it's own like you'd get on a normal install.

(both the fact that you have /dev/loop0 as your / partition, and the presence of /host directory would indicate to a Wubi install instead of a normal one)

---

### Post by I am desperate on 2012-06-30
This is exactly what I did. I thought I read this is how it is supposed to work. How am I supposed to do it, or where can I read to do it the right way then?

---

### Post by matt_symes on 2012-06-30
Hi

You need a partition for Ubuntu for a proper installation. 

WUBI, although a good solution, is only really for trying out Ubuntu for a short period of time.

You need to download an iso file from here.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

using the top option (Ubuntu desktop). Download the 64 bit version if your machine is 64 bit, otherwise download the 32 bit version, and burn it to a CD or make a bootable usb.

You can install it from there. 

The installer will create a new partition and install Ubuntu into that partition or you can create your own partition before hand.

You can also migrate your WUBI installation into a partition of you want to keep what you have.

Read this tutorial.

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

I would recommend backing up your entire hard drive first, which ever option you choose, using some cloning software.

Kind regards

---

### Post by I am desperate on 2012-06-30
Okay, so I got Ubuntu desktop and put it on a USB. I have all my data on an external drive. No need to save anything. I can treat this computer like it's all new, there is nothing to loose in Windows or Ubuntu.
What I think I should do is unistall the current Ubuntu, do a quick fragmentation of the partition Ubuntu is going to and then simply run the installation of Ubuntu from the USB stick?

---

### Post by oldfred on 2012-06-30
Ubuntu does not install to NTFS partitions except as the wubi install. Do not create partitions with Windows as it may convert to dynamic partitions not an extended with logicals. Linux does not work with dynamic partitions.

A default install is / (root) and swap. If you have unallocated space and one of the 4 primary partitions left it will just install.

If you want to manually install (Something Else) to create additional partitions like a separate /home then you have to partition, format partitions, choose which partition is /, /home and swap. You can partition as part of the install now, or use gparted in advance to create partitions.

---

### Post by I am desperate on 2012-06-30
I feel like I should have it all figured out by now, but somehow things are still not working out.

I had the partition set to NTFS and now have it as unallocated space. However it does not install. If I understand it right Ubuntu should install itself on an unallocated partition and there is nothing else I have to do to it?

I see the problem in either my USB device or in me being too stupid to use the iso file correctly. I formatted the USB to FAT32 and opened the iso using 7-Zip File Manager. Whenever I try to boot from the USB I get the note "Reboot and Select proper Boot device or Insert Media in selected Boot device and press a key" from there it just takes me to Windows.

---

### Post by oldfred on 2012-06-30
You do not copy ISO to CD or USB, you have to install it so it is extracted and becomes a bootable device.

Instructions are on the download page:

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by I am desperate on 2012-07-01
Turns out it was the USB Stick that was causing the problems; using a CD worked out fine right away.
Windows is still working, and so is Ubuntu now with the disc space and speed it should.

Big thanks to everyone helping!

---

