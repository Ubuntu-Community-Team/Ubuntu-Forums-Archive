---
title: "help......really new"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by whench on 2008-09-11
hi everyone

can anyone please help me, i am really new both to abuntu and computers, i have an abuntu disc that i have tried and like very much, i would like to turn on my computer and chose whether i use abuntu or my excisting vista each time.  i have an external hard drive running from my usb port and i would like to put ubuntu on that, i have read most of the threads and have to admit coming from a non computer gereration i am having trouble understanding the instructions and terms, so can anyone possibly put me in the right direction for some step by step instructions in (baby language)as to how i accomplish this

any help would be much appreciated :)

---

### Post by john_spiral on 2008-09-11
get the latest ubuntu cd for free from:

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

or download it, burn the large .iso file to a CD as an image.

Boot off the CD, you might need to set your computer to do this by pressing F8 or F12 or esc as the computer starts.

Double click on install ubuntu....

Follow the instructions on screen then hopefully you should have an option to switch between vista and Ubuntu when the computer starts.

---

### Post by sayakb on 2008-09-11
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by LowSky on 2008-09-11
> **whench said:**
> 
  i have an external hard drive running from my usb port and i would like to put ubuntu on that, 
  

OK here goes

make sure while rebooting after the install that the computer can boot from a USB drive, you can set that option from the BIOS screen during start up. If it cannot do this then installing to a USB drive may not work. on to the steps. To get to BIOS watch the Computer turn on it will tell you to press a button to enter BIOS usuall a F key like F2 or F11, sometime Delete, just watch for it.

1. Make sure the USB drive is turned on and connected
2.Put Ubuntu in the Disc drive  and start computer
3. from menu chose install
4. follow the menues until it gets to the where to install ubuntu. If the USB drive doesn't apear (its a good point to note the drive actual size beforehand, like is it 40GB or 200GB and to know its size compared to the internal hard drive as Ubuntu doesn't use letter to name drives this may look confusing at first, so Know your drives' sizes).
5.install should go ok. everything is very simple.
6. reboot like it say to and remove the CD
6. now change the BIOS to boot from the USB drive

---

### Post by tea for one on 2008-09-11
There are a few points to consider if you want Ubuntu on your external USB drive and a Windows OS on your internal HDD.

(a) The Ubuntu installation will create a Grub bootloader. This is the little bit of vital software which allows you to choose operating systems
(b) If you install Ubuntu to an external USB drive, the Grub will not appear unless the external USB HDD is plugged in. It will not be a problem if all drives are accessible at "power on"
(c) If your external USB HDD is not plugged in, your Windows OS on your internal HDD may not be available.

---

### Post by whench on 2008-09-11
thank you so much for your help, the instructions are great and easy to understand, i will try ( and keep my fingers crossed lol) and let you know how i go

---

### Post by LowSky on 2008-09-11
> **tea for one said:**
>   (a) The Ubuntu installation will create a Grub bootloader. This is the little bit of vital software which allows you to choose operating systems
True

> **tea for one said:**
>  (b) If you install Ubuntu to an external USB drive, the Grub will not appear unless the external USB HDD is plugged in. It will not be a problem if all drives are accessible at "power on"
True that Grub will only appear if the USB drive is selected at the boot drive. But also False, as it can be a problem if Windows is selected as your boot drive because Grub will not show up and you will not be able to boot into ubuntu. Make sure to set BIOS up correctly

> **tea for one said:**
>  (c) If your external USB HDD is not plugged in, your Windows OS on your internal HDD may not be available.  
False, The drive is chosen by the user first and BIOS second, so if his USB drive is picked to boot frst and not plugged in, BIOS might choose the next availible drive, like the internal Windows Drive.

---

### Post by tea for one on 2008-09-11
I do not think that we should make any assumptions about a PC's BIOS. For example, I cannot boot from a USB device (I do not have an option to select USB in my BIOS), however I can install an OS on an external USB HDD and add the external OS on the Grub list which resides on my internal HDD. Ubuntu resides on my internal HDD.

Therefore I suspect that new users should be aware of the choices that their own particular BIOS affords them.

---

