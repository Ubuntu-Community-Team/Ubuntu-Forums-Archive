---
title: "Linux and windows"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by jt358 on 2013-12-28
Hi all,

I'm still having issues understanding how to put Ubuntu on my windows laptop.

I need to use some programmes that I can apparently only download and use in Linux.

Could someone post (for a moron) exactly how I put Linux on it  (I have tried the WUBI download but once on the compute I couldn't log on) so I took it off.

many thanks

Jamie

---

### Post by oldfred on 2013-12-28
What version of Windows as that makes a lot of difference. 
What computer and video card/chip?

New Windows 8 is UEFI which is totally different. 
Windows 7 usually used all 4 primary partitions, so you have to work around that. 
With XP usually a primary partition is available and it is relatively easy.

Have you downloaded the live installer and installed to a flash drive or DVD?
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by crazypj10 on 2013-12-28
Personally I haven't been able to boot from a flash drive and had to buy DVD media as the latest 64 bit Ubuntu 12.04 - 2.1 LTS  is slightly too big to fit on CD
you will probably have to adjust BIOS so CD/DVD or USB are first in line for boot options after re-boot you should be able to set a partition or allow distro to do it for you

---

### Post by steeldriver on 2013-12-28
Have you considered using a virtual machine (I'd suggest Oracle Virtualbox - but that's really only because it's the one I'm familiar with) - it will give you a pretty usable Linux platform (especially if you can enable hardware acceleration) without the need to repartition / mess with your Windows installation (and without Wubi - which is not really supported any more)

[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by Bucky Ball on 2013-12-28
See post #2 and also crazypj10 recommendations to check in BIOS that you have the machine set to boot from the DVD or USB (which ever you are using to install from).

@steeldriver: OP is asking 'Could someone post (for a moron) exactly how I put Linux on ...'. They want to install Ubuntu to a hard drive rather than learn about Virtualbox. ;)

---

### Post by varunendra on 2013-12-28
> **Bucky Ball said:**
> They want to install Ubuntu to a hard drive rather than learn about Virtualbox. ;)

Definitely. But maybe they weren't even aware that virtualization is also an available option. I personally find it one of the safest ways for one to familiarize themselves with a new OS and its installation process. But yeah, we should also mention the hardware and severe performance limitations virtual machines have. :)

@ Jamie,

Like I mentioned above, if you wish to familiarize yourself with the installation process, may be experiment some more than that, you can do that safely on a virtual machine. The most popular virtualization software are VMware and VirtualBox. Virtual Machines are completely isolated from your host Operating System (which is currently Windows on your laptop), and the (virtual) hard disk it 'sees' is actually just a file on your actual hard disk, so any change you do on it is completely isolated from the actual hard disk. So you can safely experiment as much as you like before installation on the actual hard disk.

A full physical installation on (actual) hard disk, which you originally asked help for, is highly recommended if you want the full capability and performance of the OS. But if you want a clear step-by-step instruction set specific to your system, answers to **oldfred's** questions are of vital importance.

In any case, it is best to write a Live CD/DVD or create a Live USB and test the OS in "Live" mode ("Try", not "Install" option) first to make sure it works properly with your hardware. For creating Live media (CD/DVD/USB), oldfred has already provided few of the best links.

---

### Post by plurga on 2013-12-29
hi 
to install ubuntu into a pc/laptop that already has windows os , u can : 
1.- install ubuntu using GRUB menu , it means , when u turn on the pc u have to choose which os u want to start up. 
2.- as steeldriver says , u can install an hypervisor program as vmware workstation , virtual box , etc.. create a virtual machine and install ubuntu. 

i rather this option bcs u can run both machines windows and ubuntu at the same time. but it depends from ur pc resources.

---

### Post by jt358 on 2013-12-29
Hi all,

many thanks for all the info, I'll have a read through and try and understand it:)

seriously many thanks

Jamie

---

