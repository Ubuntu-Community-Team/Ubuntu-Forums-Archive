---
title: "How to run ubuntu in Windows 7 Pro 64 bit"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by Jon Banquer on 2011-11-28
What is the easiest way to do this? From poking around I guess what I want to do is run ubuntu in what I think is called a virtual box?

---

### Post by Sealbhach on 2011-11-28
Yes, just download virtualbox for Windows from here:

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Then download a 32-bit Ubuntu iso and boot up your Ubuntu virtual machine from that. It's pretty easy, the Virtualbox interface is quite intuitive.

.

---

### Post by 3rdalbum on 2011-11-28
If you want Ubuntu inside a window on your Windows desktop, then Virtualbox is the way to do it.

If you want to try Ubuntu on your real hardware at full speed, then you need to boot up the computer from the Ubuntu CD and run the installer; this will allow you to partition your hard disk. Then you'll be able to choose between Ubuntu and Windows whenever you start up, and that operating system will be truly running on the hardware.

Otherwise, you could always use the Ubuntu installer and opt to remove Windows entirely.

---

### Post by Jon Banquer on 2011-11-28
Thanks. Downloading it now. When I get more comfortable with ubuntu I'll install it permanently. Right now I can't even figure out how to get You Tube videos to play and how to install software like Inkscape in ubuntu so I've got a long way to go. 

I have been able to figure out a good deal about Nautilus File Manager.  Nautilus File Manager has solved my long file name problems that Windows 7 Pro 64bit was giving me. I going to do all my file backup and management with ubuntu instead of Windows 7 Pro 64 bit as ubuntu is more robust, more powerful and doesn't give me any error problems like Windows 7 Pro 64 bit does.

Is there a current ubuntu manual in .pdf that I can download? All I can find is one for 10.10 

Thanks for all the help. It's very much appreciated.

---

### Post by mlentink on 2011-11-28
> **Jon Banquer said:**
> how to install software like Inkscape in ubuntu
Click on the ubuntu logo icon, type 'Software', click on the Ubuntu Software Center, type 'inks' in the searchbox and doubleclick on Inkscape. It's that easy. Compare that to installing software in W7 huh?....

---

### Post by Jon Banquer on 2011-11-28
If I'm booting and using ubuntu from my USB drive does Inkscape stay installed or do I have to install it every time I boot ubuntu from my USB drive?

---

### Post by mlentink on 2011-11-28
Is this a USB-stick or a real drive?
If it's a stick, is it the one with the Live Ubuntu or have you already installed for real on it?
The Live USB program has the option of reserving room to make changes persistent, in which case Inkscape would stay installed.
If it's a real install on a USB-drive, than obviously it will stay installed.

---

### Post by Jon Banquer on 2011-11-28
ubuntu is not installed and runs off the USB stick. Where do I find the option of reserving room to make changes persistent as I want Inkscape to stay installed on my C: drive? It would also be okay if Inkscape installed on the same USB stick that has ubuntu on it but I'm not sure if that will screw up ubuntu.

---

### Post by taxman123 on 2011-11-28
Yes I agree with you all just going through my resources, I found these great links, I'm only a noob, but these resources were great for me.
 
[Installing Ubuntu inside Windows using VirtualBox ]("http://www.psychocats.net/ubuntu/virtualbox")
 
[Books ]("http://www.123books.com.au")[on Ubuntu Linux]("http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html")
 
[:)]("http://www.123books.com.au")

---

### Post by *^kyfds( on 2011-11-28
> **3rdalbum said:**
> If you want Ubuntu inside a window on your Windows desktop, then Virtualbox is the way to do it.

If you want to try Ubuntu on your real hardware at full speed, then you need to boot up the computer from the Ubuntu CD and run the installer; this will allow you to partition your hard disk. Then you'll be able to choose between Ubuntu and Windows whenever you start up, and that operating system will be truly running on the hardware.

Otherwise, you could always use the Ubuntu installer and opt to remove Windows entirely.

**Or** you could install it via a usb, allowing you pretty much do the same thing, without wasting a disk.

here's the link :) 

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

just select boot from a USB, and you'll be redirected to a guide on how to install onto a USB.

---

### Post by Mark Phelps on 2011-11-29
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

