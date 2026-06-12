---
title: "Wireless 12.04 Puzzle"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by davidjames91 on 2013-03-31
I am running 12.04 ubuntu. I bought a Dlink 160 wireless usb adapter without checking compatibility, because they have always worked out of the box for years for me.

After a little research, I found out that the firmware needs to be installed to root and all the steps to make it work. However, I do not have an available wired connection, just wifi provided by my ISP. I can't even dowload the drivers let alone get commands requiring internet access in Terminal to run.

I do have cds for windows xp and 7. I was wondering if I could boot those from a USB drive and run something as a translator t o my Ubuntu that is running off my hard drive?? Or (less preferably!) Download windows to the hard drive and run Ubuntu off my flash drive?

It might not even need to be the entire operating system - just some way to translate using either a usb flash drive or a maybe an android phone.

Any help would be really appreciated!
I am a college student and I can't afford to be losing money on stuff, even if I could just buy another wifi adapter that would boot right up out of the box. I want to get this problem fixed and not have to install windows back on here because I think Linux is pretty cool.

---

### Post by davidjames91 on 2013-03-31
and if it helps it has the thirty two bit version running.

---

### Post by wildmanne39 on 2013-03-31
Hi, please post the output of:
```
lsusb
```
Thanks

---

### Post by davidjames91 on 2013-03-31
Thank you for helping, I really appreciate it. I've spent hours on this. 
david@david-OptiPlex-745:~$ lsusb
Bus 002 Device 011: ID 2001:3c1a D-Link Corp. 
Bus 004 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 004 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by wildmanne39 on 2013-03-31
I have been researching this device, there are several different chipsets made for this device that is why it does not work out of the box if it came with one of the other chipsets that many of the same model numbers come with then it would work out of the box.
Here is a link with what you need to do to make it work.
[http://bernaerts.dyndns.org/linux/229-ubuntu-precise-dlink-dwa160-revb2](http://bernaerts.dyndns.org/linux/229-ubuntu-precise-dlink-dwa160-revb2)

You should be able to use a computer with internet to download the files to a flash drive then put them on your ubuntu computer, I have not done it that way before but I do know that it is harder without internet on your computer if possible I recommend taking it to a friends where you can plug it in to get it working.

Do you have an internal wireless card?
Thanks

---

