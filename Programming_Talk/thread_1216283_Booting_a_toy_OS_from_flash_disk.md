---
title: "Booting a toy OS from flash disk"
date: 2009-07-18
forum: Programming Talk
---

### Post by 2weird on 2009-07-18
I have recently read this tutorial on Operating systems: [http://linuxgazette.net/issue77/krishnakumar.html](http://linuxgazette.net/issue77/krishnakumar.html)

The problem is that I want to be able to run the toy OS from a flash disk. I have successfully written the boot program to the flash disk ("/dev/sdb"), as in the tutorial, but nothing is happening.

Can someone tell me what I should do in order for it to work?

Thanks.

---

### Post by mmix on 2009-07-18
Reset the machine. Enter the BIOS setup and make usb the first boot device. Put the usb in the drive and watch the computer boot from your boot usb.

---

### Post by 2weird on 2009-07-18
> **mmix said:**
> Reset the machine. Enter the BIOS setup and make usb the first boot device. Put the usb in the drive and watch the computer boot from your boot usb.

I did, that's why I am posting :P
Not only did I change the device priority but also my HP BIOS allows me to pick which device to boot from even if the priorities are different.

Either way grub gets loaded immediately.

---

### Post by stevescripts on 2009-07-18
Edit your menu.lst, perhaps? 

EDIT:  Surprised that changing the BIOS settings did not work ...

Steve

---

### Post by 2weird on 2009-07-18
> **stevescripts said:**
> Edit your menu.lst, perhaps? 

EDIT:  Surprised that changing the BIOS settings did not work ...

Steve

I tried running the OS on a friend's computer and it works.
Yes, grub seems to be the problem.
Ok, so how do I add a flash disk to menu.lst?

---

### Post by stevescripts on 2009-07-18
EDIT Grub: [http://www.howtoforge.com/working_with_the_grub_menu](http://www.howtoforge.com/working_with_the_grub_menu)

This may be even more useful, however: [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

Hope this helps a bit.

Steve

---

