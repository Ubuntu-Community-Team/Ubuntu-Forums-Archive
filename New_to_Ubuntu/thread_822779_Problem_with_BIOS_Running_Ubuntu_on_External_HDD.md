---
title: "Problem with BIOS: Running Ubuntu on External HDD"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by silent contender on 2008-06-08
I install Ubuntu on an external HDD on a new Gateway computer.  The install runs fine, until I tried on a much older HP desktop (~2001).  I cannot get the BIOS to boot from the external HDD.  I didn't see the external HDD in the BIOS like I did on the Gateway.      I think the BIOS is Phoenix 3.0.

How can I get the BIOS to read my external HDD, or is Phoenix 3.0 just not able to boot from an external HDD?

Thanks.

---

### Post by TeoBigusGeekus on 2008-06-08
I think older motherboards do not support booting up from a usb device.
Someone correct me if I'm wrong...

---

### Post by MDSmith2 on 2008-06-08
Your right older motherboards don't support boot from usb

---

### Post by silent contender on 2008-06-09
New problem.

Now it does not even boot on the new Gateway.  I will try again and  post if this continues.

Thanks.

---

### Post by sam_delta on 2008-06-09
for old motherboards, there are diskettes or CDs, which you can boot from, will load linux kernel to handle USB ports and then will boot from your usb Drive
i believe that supergrub has this type of option/diskettes

sam

---

### Post by silent contender on 2008-06-11
I have only found permanent and not portable solutions using Super Grub Disk.  However, booting from a kernel did catch my eye.  Though, Puppy Linux was the only thing mentioned for this method in the Super Grub Disk Wiki.

I would appreciate help with booting the Ubuntu kernel and then loading the external HDD or other ideas/methods.

---

### Post by Duck2006 on 2008-06-11
[http://www.pendrivelinux.com/category/install-to-usb-hard-drive/](http://www.pendrivelinux.com/category/install-to-usb-hard-drive/)

If your bois will not boot a usb drive then you will need a cd or a 3.5 disk to boot to first and then boot your usb drive.

---

### Post by silent contender on 2008-06-11
I understand that I need a CD or 3.5 floppy.  But how and what do I boot from the CD or 3.5 to allow me to boot my external HDD.

---

### Post by Duck2006 on 2008-06-11
This may help.

[http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html](http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html)

---

### Post by logos34 on 2008-06-11
> **silent contender said:**
> I have only found permanent and not portable solutions using Super Grub Disk.  However, booting from a kernel did catch my eye.  Though, Puppy Linux was the only thing mentioned for this method in the Super Grub Disk Wiki.

I would appreciate help with booting the Ubuntu kernel and then loading the external HDD or other ideas/methods.

Here's one I recommend a lot:

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

(portable)
-->'Booting the kernel from a bootable CD'

-->'Booting the kernel from an internal hard drive'
(you make a /boot partition on the internal drive and put kernels there)

---

### Post by silent contender on 2008-06-11
Thanks, that helped ALOT!!!:grin:

In addition I found this thread from your link.
[URL="http://ubuntuforums.org/showthread.php?t=80811"]
http://ubuntuforums.org/showthread.php?t=80811[/URL]

---

### Post by silent contender on 2008-06-12
I fix the Gateway computer's problem.  It was hardware related (the USB Port came off the IC board, had to resolder it :)).  However, I am still working on booting from the ancient BIOS through a kernel.

---

### Post by silent contender on 2008-06-12
The external HDD now works on the ancient BIOS.  I also found this page very helpful.
[URL="https://help.ubuntu.com/community/BootFromUSB"]
https://help.ubuntu.com/community/BootFromUSB[/URL]

---

