---
title: "Mistakes were made"
date: 2016-10-19
forum: New to Ubuntu
---

### Post by limiv on 2016-10-19
Hey, so i just installed Ubuntu 16.04 to my laptop (lenovo-g50-70) because i wanted to start using linux however i chose the wrong option during the installation and i completely erased my windows.

I tried making a bootable usb flash drive on windows (other laptop) but somehow it does not work on my laptop (lenovo-g50-70) so i can not revert to windows.

Q: Is there a way to put windows on my laptop again, and if so how?

---

### Post by Habitual on 2016-10-19
re-install using an original media, or one made from a recovery partition.
Does your system have a Recovery Option?

---

### Post by RobGoss on 2016-10-19
You might want to change the title of your post to decibel your problem it will get you the best help possible 

It's always recommend to make a full backup of your system especially if your trying to dual boot

Do you have a recovery disk for Windows if you do you will need to run that to restore your machine

---

### Post by col48 on 2016-10-19
And be aware that restoring windows will either totally overwrite the Ubuntu or (if opting to dual boot) leave Ubuntu invisible when booting.  (Many other threads arise from this scenario!)

So, if you have anything on the Ubuntu you have changed since installation, take a full backup.  Maybe take one anyway - it could be good practice!

---

### Post by limiv on 2016-10-19
My laptop does indeed have a recovery but it no longer functions as all partitions have been wiped and windows is no longer present on my laptop.
Unfortunately my knowledge of Linux is very limited and although i want to broaden my knowledge of Linux my main priority right now is getting Windows back on my laptop. The problem here however is that no matter how i make my USB flash drive it wont boot. (it does not show up in my bios either) 
Are there other ways of restoring Windows to my laptop or is there something i am overlooking?
If i can just get Windows on my laptop once again i can handle the rest.

---

### Post by RobGoss on 2016-10-19
You might want to try this link [https://www.microsoft.com/en-us/software-download/windows10/](https://www.microsoft.com/en-us/software-download/windows10/)

It should help you with Windows problem

---

### Post by Frogs Hair on 2016-10-19
If you were using Win 10 and the device is logged on MS severs you can download and install the same version of Win 10 you were using. I have tested this and had no product key/activation issues.

---

### Post by leunam12 on 2016-10-20
What version of Windows do you need?

---

### Post by limiv on 2016-10-22
Windows 8.1, i have the iso already but i just can not get my usb to be seen as a bootable device.

---

### Post by yancek on 2016-10-22
If your usb drive does not show in your BIOS, then trying to boot from a usb obviously won't work.  How old is this machine?  Any machine built in the last 8 years should be able to boot from a usb.  Have you checked all the options to change boot priority?  
How did you try to create the bootable usb, what software did you use?
Does Ubuntu boot?  If so, you can use the link below to put the extracted windows iso on a flash drive and boot from the Ubuntu Grub.  This is not as simple as creating a bootable usb drive.  Do you not have a DVD drive?

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by RobGoss on 2016-10-22
> **limiv said:**
> Windows 8.1, i have the iso already but i just can not get my usb to be seen as a bootable device.

You might have to access your BIOS and set your USB device to be first boot on most machines** F-2** will get you to your BIOS after saving the changes reboot and try tapping the **F-12** key this should give you the option to choose your USB device.

Best of luck

---

### Post by leunam12 on 2016-10-26
Use Rufus on Windows to make the bootable USB. Check on BIOS sometimes there is an option where you have to enable boot from USB. If it fails try using PLOP boot manager on a CD.
[https://www.plop.at/en/bootmanagers.html](https://www.plop.at/en/bootmanagers.html)

---

