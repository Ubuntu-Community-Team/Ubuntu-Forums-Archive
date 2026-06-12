---
title: "Insalling Plop linux"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by alex191 on 2014-05-02
I have a Sony vaio v505bx that does not support usb booting from BIOS. Im currently running Ubuntu 14.04. How so i install plop linux so i can boot from my usb drive?

---

### Post by piotrasbl on 2014-05-02
Hi there,
does this one have option to emulate FDD from USB ?

---

### Post by Dennis N on 2014-05-02
If you mean Plop boot loader (or boot manager), the .zip file you download contains an .iso, which you burn to a cd, and then boot that cd from your cd or dvd drive. Then, you insert the usb with the Ubuntu installer, and select USB from the Plop menu. The computer then boots the USB flash drive.

---

### Post by bapoumba on 2014-05-02
I followed this : [http://xubuntu.org/news/booting-the-xubuntu-usb-image-from-a-cd/](http://xubuntu.org/news/booting-the-xubuntu-usb-image-from-a-cd/)
No issue. booted from the CD and then installed from usb.

---

### Post by alex191 on 2014-05-02
is there a way to install it from my hard drive? Ive installed Plop from my hard drive on windows 7 before. No CD or USB needed.

---

### Post by bapoumba on 2014-05-03
Did you have a read at the link in my previous post ?
[http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)

---

### Post by alex191 on 2014-05-05
Yeah my BIOS menu doesnt have an option to boot PLOP from a CD. Floppy only

---

### Post by bapoumba on 2014-05-05
> **alex191 said:**
> Yeah my BIOS menu doesnt have an option to boot PLOP from a CD. Floppy only
I have no floppy port to test, but PLOP allows you to make one and boot from it.

---

### Post by Vladlenin5000 on 2014-05-05
The Sony Vaio v505bx is capable of booting from a (bootable) CD. That's how the Sony Recovery Kit, among others, work. As a matter of fact, considering the tutorial from Sony I just browsed, it seems the boot from CD is the default option: Insert the CD, reboot and it boots the recovery environment from the CD... So, Plop or any other installation media should work the same way. Have you tried?

---

### Post by C.S.Cameron on 2014-05-05
I installed plop to HDD of an old computer whose BIOS would not boot flash.


[http://www.plop.at/en/bootmanager/mbrinstall.html](http://www.plop.at/en/bootmanager/mbrinstall.html) 

I don't think Plop is necessary if the computer already has grub.

---

### Post by Vladlenin5000 on 2014-05-06
The point was - and still is - you shouldn't need that for the Sony Vaio. It should boot from a CD and *probably* also from USB because most of the notebooks and desktops from that era also did it, you might have to select "USB-HDD" or "USB-FDD", one or the other should do it.

---

### Post by bapoumba on 2014-05-06
> **Vladlenin5000 said:**
> The point was - and still is - you shouldn't need that for the Sony Vaio. It should boot from a CD and *probably* also from USB because most of the notebooks and desktops from that era also did it, you might have to select "USB-HDD" or "USB-FDD", one or the other should do it.

My own Sony Vaio does not boot from usb, no bios option for it.

---

### Post by Vladlenin5000 on 2014-05-06
Ok, but it certainly boots from CD so what's the point in installing in MBR? Not to mention that if you already have Ubuntu (or other Linux) installed the GRUB is already there in the MBR and removing it will make the Ubuntu not bootable in the standard way -> you'd have to boot from a live DVD (or from Plop+USB) until you reinstall/reconfigure Grub.

Are you expecting to boot from a USB that often? If so you might want to consider installing whatever you're trying to boot from that USB...

---

### Post by bapoumba on 2014-05-06
> **Vladlenin5000 said:**
> Ok, but it certainly boots from CD so what's the point in installing in MBR? Not to mention that if you already have Ubuntu (or other Linux) installed the GRUB is already there in the MBR and removing it will make the Ubuntu not bootable in the standard way -> you'd have to boot from a live DVD (or from Plop+USB) until you reinstall/reconfigure Grub.

Are you expecting to boot from a USB that often? If so you might want to consider installing whatever you're trying to boot from that USB...
Yes, but I had no blank DVD, had a blank CD and usb thumbdrive, so that is why I used PLOP to boot from CD when I was ready to run a clean install.

---

### Post by Vladlenin5000 on 2014-05-06
> **bapoumba said:**
> Yes, but I had no blank DVD, had a blank CD and usb thumbdrive, so that is why I used PLOP to boot from CD when I was ready to run a clean install.

Although my previous post has a direct reply to yours the message itself was directed to the OP, obviously, as I think he/she is overcomplicating things :wink:

---

### Post by bapoumba on 2014-05-06
> **Vladlenin5000 said:**
> Although my previous post has a direct reply to yours the message itself was directed to the OP, obviously, as I think he/she is overcomplicating things :wink:

Yeah, I know, but if they are used to use it this way, why not ?
:)

Edit: reading over, it also appear they cannot boot from CD, only floppy. So that would make sense to them.

---

