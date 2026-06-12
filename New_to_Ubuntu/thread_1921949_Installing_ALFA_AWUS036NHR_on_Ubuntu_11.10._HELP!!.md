---
title: "Installing ALFA AWUS036NHR on Ubuntu 11.10. HELP!!!!"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by eliashernandez on 2012-02-07
I need help. I haven't been sleeping because I cant figure it out!:( I am very new to Ubuntu and I really need to get this USB wireless running. Im running Ubuntu 11.10 on a virtual machine. It's 64 -bit.  Please if someone could tell me how to install the DRIVERS (which is what i need to knwo how to do it) will be awesome. It comes with some instruction, but as far as I know that is just to make the driver yourself and Im not at that level yet.:(

---

### Post by wildmanne39 on 2012-02-07
Hi, your virtual machine uses your host internet connection it does not use its own connection so if you have a working connection on your host machine you should have a working connection on your guest.
Thanks

---

### Post by eliashernandez on 2012-02-15
My internet connection works fine! that is not the problem. The problem comes when I turn off the computer's wifi and try to use the device to get wireless. The problem is that i do not know how to make it work. Because I tried it on my OSX mac and Windows and it works fine, I Just do not know how to install it in ubuntu

---

### Post by haqking on 2012-02-15
> **eliashernandez said:**
> My internet connection works fine! that is not the problem. The problem comes when I turn off the computer's wifi and try to use the device to get wireless. The problem is that i do not know how to make it work. Because I tried it on my OSX mac and Windows and it works fine, I Just do not know how to install it in ubuntu

you probably need to blacklist rt2800.

That chipset on the Alfa works out of the box on most linux distros i use, though there is a problem with it in Debian, but works fine in others.

---

### Post by 3rdalbum on 2012-02-15
Listen.

Ubuntu in the virtual machine cannot access USB devices. Any operating system in a virtual machine cannot have access directly to the underlying hardware, otherwise the computer would immediately crash and you would lose data.

Ubuntu cannot see the USB wireless because the virtual machine is not exposing the USB to Ubuntu.

An internet connection in the host OS will appear as an Ethernet connection in the guest OS. That's how it works.

To check if the USB wireless is supported in Ubuntu, you could start your computer from the Ubuntu CD and select the "Try Ubuntu" option from the window that appears after a few minutes. This will not damage any of your data. I think that wireless device works out-of-the-box on Ubuntu 11.10 anyway.

---

### Post by haqking on 2012-02-15
> **3rdalbum said:**
> Listen.

**Ubuntu in the virtual machine cannot access USB devices. Any operating system in a virtual machine cannot have access directly to the underlying hardware**, otherwise the computer would immediately crash and you would lose data.

Ubuntu cannot see the USB wireless because the virtual machine is not exposing the USB to Ubuntu.

An internet connection in the host OS will appear as an Ethernet connection in the guest OS. That's how it works.

To check if the USB wireless is supported in Ubuntu, you could start your computer from the Ubuntu CD and select the "Try Ubuntu" option from the window that appears after a few minutes. This will not damage any of your data. I think that wireless device works out-of-the-box on Ubuntu 11.10 anyway.

**sorry but that is completely incorrect**

All due respect but that is wrong

USB wireless devices are and always have been supported in virtual machines.

I use them all the time, it is a way to use wireless in tools such as Backtrack when you havent got a local install and cant access the built in hardware.

As long as you select the device from the USB menu it is the same as any other USB device and you install/setup as so.

Cheers

---

### Post by Valinath on 2012-03-17
Hey guys!

I have a very similar problem, I do not have Ubuntu on VM, i use it as main OS.

And i cant get it to work with Ubuntu, I have tried some drivers to it, but i cant install any of them. the make and make install commands doesnt work due to the driver cant find "smb-lock.h"

Its just really pain in the ):P

Anyone with the same problem here that have solved this? I use kernel 2.6.39-3

/Valinath

---

