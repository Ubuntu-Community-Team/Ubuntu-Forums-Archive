---
title: "Need help with drivers for Asus Zenbook Pro"
date: 2016-02-21
forum: New to Ubuntu
---

### Post by k-stefanov87 on 2016-02-21
Hello,

I am new to ubuntu, using it for few weeks now in dual boot, trying to read and follow steps for simple tasks and i am doing pretty well such as open office installs, sykyep, chrome and other software i need and use.
Now the problem is that i noticed i need few things like usb support for flash drives, and i assume i will be needing some software like drivers for my hardware but i have no idea where to find it and how, may i get some assistance in that matter please ?

My Asus Zenbook Pro is 4GB ram, Processor is: Intel® Core™ i7-3517U CPU @ 1.90GHz × 4 , graphic card is: Intel® Ivybridge Mobile with a 250GB or something like that SSD.

I would be really greatfull for any assistance give, and thank you in advance.


Thanks.

---

### Post by christiaan3 on 2016-02-23
You can manually mount your USB drive with the terminal. If you go to the terminal and you type the following command:
 **sudo fdisk -l** 
You will see a list of your connected devices. The devices listed at the bottom are the once you want to look at. Here you should probably see something like sda1. (with the correct size of your usb) 
When you found your disk you will create a folder to mount your drive to. [B]
sudo mkdir -p /media/usb[/B]. 
Next thing you do is mount it there with the command 
**sudo mount -t vfat /dev/sda1 /media/usb**
The stuff on your usb will now appear in the folder usb in your media folder.

---

### Post by k-stefanov87 on 2016-02-23
do i have to do it every single time i mount an usb flash drive ? is there nothing similar to windows that the flash drive will pop up every time you connect it or ?

---

### Post by buzzingrobot on 2016-02-23
> **k-stefanov87 said:**
> 
My Asus Zenbook Pro is 4GB ram, Processor is: Intel® Core™ i7-3517U CPU @ 1.90GHz × 4 , graphic card is: Intel® Ivybridge Mobile with a 250GB or something like that SSD.



With the exception of some edge cases, the appropriate hardware drivers are installed and used by default. If you find that a specific component is not working, you should post a specific question about that. 

The Intel video should be supported out of the box. Intel provides an open source video driver that ships with Ubuntu and will be used automatically when the kernel detects the Intel video.  You don't need to chase down anything. 

Drives need to be mounted (made known and accessible) before they can be used, include USB sticks. You can expect this to happen automatically in Unity. I.e, you attach a USB stick and, momentarily, you'll see a popup.  The stick should also appear in Nautilus, the file manager. You do not need to chase down USB drivers.

It's the very latest components for which the vendor does not supply a Linux driver that can be an issue.

---

### Post by k-stefanov87 on 2016-02-28
> **buzzingrobot said:**
> With the exception of some edge cases, the appropriate hardware drivers are installed and used by default. If you find that a specific component is not working, you should post a specific question about that. 

The Intel video should be supported out of the box. Intel provides an open source video driver that ships with Ubuntu and will be used automatically when the kernel detects the Intel video.  You don't need to chase down anything. 

Drives need to be mounted (made known and accessible) before they can be used, include USB sticks. You can expect this to happen automatically in Unity. I.e, you attach a USB stick and, momentarily, you'll see a popup.  The stick should also appear in Nautilus, the file manager. You do not need to chase down USB drivers.

It's the very latest components for which the vendor does not supply a Linux driver that can be an issue.

I understand, thank you very much for the info, didn't know all that :)

---

