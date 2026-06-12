---
title: "Can't write or save files on Ubuntu on USB"
date: 2018-06-26
forum: New to Ubuntu
---

### Post by raaboy on 2018-06-26
I am new to Ubuntu. I created a ubuntu USB stick and I can run the desktop and it is great but when I download a new app or save a file I created in a text editor or make changes to settings they are not there when I reboot and enter the desktop. It is all gone. Is this because I am TRYING Ubuntu and have not installed it to me laptop's hard drive? I need and want to run Ubuntu from the USB like it was on a HDD. Please help this newbie.

Thanks in advance, Vince

---

### Post by wildmanne39 on 2018-06-26
Hello and welcome to the forum, you have to make the usb persistent to be able to save files and apps from one reboot to another, otherwise the files and apps are just stored in ram and disappear when you reboot.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by raaboy on 2018-06-26
Can I do this persistence on the same USB drive since I have more than 25 GB of free space on it or do I need to somehow create another USB for this, if so, do I always have to use two flash sticks to do work like GIMP, Libre Office, and other apps. What about installing other apps like GIMP?

---

### Post by raaboy on 2018-06-26
Thinking about this and I wanted to learn Ubuntu Linux well enough before I install it onto Windows 10. I thought if I learned enough of Linux and feel good about it I would use a virtual machine on Windows 10 and install Ubuntu there using something like VirtualBox. Would I solve the problem of downloading and installing apps, writing files and such if I created a virtual machine in Windows 10 and put Ubuntu into it?

---

### Post by wildmanne39 on 2018-06-26
I believe you can use the same usb drive but I think you have to reinstall ubuntu, sudodos is a good person to get help from on the forum for creating persistent usb drives but he has his own app he uses, it is probably best to see if he replies when he comes online.

You may want to look here, this method is much newer and more up to date.

[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by wildmanne39 on 2018-06-26
Yes virtualbox is a good way to go but realize windows will slow the vm down some because it is always running something in the background I know because I used ubuntu in virtualbox for more then a year but only because I had too.

---

### Post by raaboy on 2018-06-26
wildmanne39, thank you for your time and patience. What is the best way to run Ubuntu besides installing on the hard disk? I can't afford to buy another new laptop and the one I have is Windows 10 and need that for work. But I want to get into the Linux world. I want to use GIMP and a CAD program in Linux and be able to install the apps and create files in Linux. I can do that if I use it in a virtual machine, right? But you said that is not the best way. Should I stay with the USB method or are you saying that installing side by side with Windows 10 as a dual boot system?

---

### Post by yancek on 2018-06-26
Your description of your Ubuntu usb is exactly what a "Live" Linux system is, read-only with no changes saved.  There are a number of ways you can create and use persistence but the best thing to do would be to get another usb drive and install to that.  Using mkusb suggested above would probably be the best but you would need to download it while booted to your "Live" Ubuntu and install it to a second usb.
You could also use the "toram" boot option which should install another instance of Ubuntu to the same usb but if you are not familiar with Linux, I would definitely NOT recommend trying that.  You could download unetbootin on your Ubuntu usb and use it to install another instance of Ubuntu to a second usb creating persistence during the process.  You could also shrink your windows partition and create a persistent Linux partition labelled "casper-rw" on that drive.  That would only work while booting Ubuntu from the computer with windows which then has the casper-rw partition and you would need to change the boot options in the BIOS to boot the usb and would need to add the persistent line to the boot menu each time you boot as well as manually mount the casper-rw partition.

Using Viritualbox in windows to install Ubuntu is probably the least risky for someone new but it will be slower because you will be running to operating systems.
No need to get a new computer, just get another usb drive.   You could then try mkusb which will create persistence and will also create an ntfs partition so you can access/share data with window.  See the link below.  

  [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

If you decide to install Ubuntu with windows, make sure you read the Ubuntu documentation very carefully at the link below before starting.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

ANother option which basically involves obtaining another usb (minimum of 16GB) would be to use your current Ubuntu usb, boot it an do a full install to another usb.  You are going to have to familiarize yourself with Linux drive/naming conventions so you don't overwrite the wrong drive.

---

### Post by sudodus on 2018-06-26
As already suggested, you can create a persistent live drive with Ubuntu, if you 

- boot from one USB pendrive with a live-only system (this can be a small and cheap pendrive, 2 GB or bigger),
- install [mkusb](https://help.ubuntu.com/community/mkusb) into this live-only system,
- use mkusb to create a persistent live system in a second USB pendrive (this should be a bigger and faster pendrive, a fast USB 3 pendrive with at least 16 GB is best).

See these links (and links from the links),

[mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)
[FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

You can also install Ubuntu like into an internal drive, but into a fast USB 3 pendrive, according to the following link,

[ Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by C.S.Cameron on 2018-06-26
If you want to run Ubuntu from the USB like it was on a HDD, install Ubuntu to the USB like it is a HDD. Start with the Live USB you have already made and use it to Full install Ubuntu to a second USB drive.
It will be more stable, secure and boot faster than a Persistent drive but won't be much good for installing Ubuntu.

See Full Install: [https://askubuntu.com/questions/287064/how-do-i-make-a-bootable-ubuntu-usb/1048863#1048863](https://askubuntu.com/questions/287064/how-do-i-make-a-bootable-ubuntu-usb/1048863#1048863)

---

### Post by Geoffrey_Arndt on 2018-06-27
Here's my scale (**1 = Lowest, 5 = Highest**) re systems capabilities and overall satisfaction:

>   Read Only Live Media (USB-Stick) =  [SIZE=4]**2**[/SIZE] . . . . best for installations and/or data rescue.   not an accurate way to eval any distro.

>   Persistent Live Media (USB-Stick) = [SIZE=4]**3 **[SIZE=2]. . . . OK for installing a few critical apps. OK also for saving changed data.  Updating Apps and OS generally a hassle or not doable.

>   Full Install Media (USBStick) = [SIZE=4]**4 **[/SIZE]. . . .  Almost an elegant way to run an OS (but not quite).   USB-Sticks still slower than other alternatives and lower life cycle.

>   Full Install Media (SSD-USBv3) =[SIZE=4][SIZE=2]  [SIZE=4]**5**[/SIZE] . . . . Equal *or better* to a full HDD install.   Only slightly slower than a standard SSD though much slower than the newer super fast SSD's (NVMe)

Am currently running the newest Ubuntu (18.04) and Elementary on two very portable & fast USBv3 SSD's.    Highly recommend this method (almost like buying a whole new PC) for about $99 usd.   Especially recommended over dual-booting on same internal disk or ssd.  (safety and stability - and can isolate the install from the main OS).

[https://www.amazon.com/SanDisk-250GB-Extreme-Portable-SDSSDE60-250G-G25/dp/B078SVRH4B/ref=dp_ob_title_ce](https://www.amazon.com/SanDisk-250GB-Extreme-Portable-SDSSDE60-250G-G25/dp/B078SVRH4B/ref=dp_ob_title_ce)
[/SIZE][/SIZE][/SIZE][/SIZE]

---

