---
title: "starting installation from grub"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by marufaberlin on 2008-10-13
Hi guys!

I have a small computer with only a cf card and a serial port and I want to install debian on it.

I have copied the installation disk to the cf card and installed GRUB on it. I can boot the kernel, but I dont know which options to set

1. I have console=ttyS0,9600n8 added.
2. I need to start installation in text mode
3. I need to append the correct root= parameter but I don't know the UUID of the partition. How can I find that out?

How do I go from there?

thanks in advance,
marufaberlin

---

### Post by Keen101 on 2008-10-13
I am really not as familiar with grub as i would like to be.

I find the unetbootin program works nicely for things like this.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by caljohnsmith on 2008-10-13
You might find it useful to check out this link:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

But to try and answer your questions...
> **marufaberlin said:**
> Hi guys!

2. I need to start installation in text mode

Do you mean see all the booting messages? Or boot into a console (no GUI)? If you want a console, you could just use "ro single" at the end of the kernel line in Grub's menu.lst. If you want to see the booting messages, then make sure you don't use "quiet" in the kernel line.
> **marufaberlin said:**
> 
3. I need to append the correct root= parameter but I don't know the UUID of the partition. How can I find that out?

You can use:
```
sudo blkid
```
To see the UUIDs of all partitions on all drives. Does that help?

---

### Post by marufaberlin on 2008-10-14
I think I have not been specific enough.
I need to start the installation in text mode and on /dev/ttyS0 without using an install cd. I have copied the contents of the install cd into a partition of the cf card (which the computer uses as hd) and put grub on the mbr of that card to boot it. I can find the appropriate kernel, but I don't know which parameters to pass

---

### Post by marufaberlin on 2008-10-15
bump

---

