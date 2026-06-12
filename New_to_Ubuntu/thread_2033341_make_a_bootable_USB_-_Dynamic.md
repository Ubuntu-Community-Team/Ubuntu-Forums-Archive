---
title: "make a bootable USB - Dynamic"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by mal_conductor on 2012-07-26
Is it possible to make a bootable USB key?

I want to use a USB key Ubuntu from.
I want to store files and applications on this USB key.

I would always use the same PC, but don´t want to have ubuntu on the hard drive.

---

### Post by anewguy on 2012-07-26
Either use unetbootin or startup disk creator to create the usb flash drive, being sure it is large enough (it's just me, but I'd recommend at least 8gb) and select persistence and select the size for it as you are creating the flash using either of the two tools.

---

### Post by yuvraj23 on 2012-07-26
Well this works only when you are installing Ubuntu.. On  ubuntu-installer You have an option to put Grub in any of available storage device.  If you put grub to a usb drive then u will need to insert usb drive on every boot.. But this is not recommended as you might accidentally corrupt the pendrive.

---

### Post by anewguy on 2012-07-26
The whole idea with a flash-drive install, not to be confused with using a flash drive TO install, including grub and persistence, is so that you don't have a trace of ubuntu on the system itself.  putting grub on the machine and linux on the flash FORCES the flash needing to be in every time you boot - windows or linux - as grub needs files in the boot folder of the linux install, NOT the way you describe it.  The OP makes it sound like they want to run Ubuntu off the flash only - so using one of the tools is needed to "burn" the image to the flash drive, allowing for persistence.  In this manner the flash drive can also be moved to another system and still run the linux install.  Of course if the hardware is different - particularly the video or wireless - some things may not work as wanted.

---

### Post by retchid on 2012-07-26
[http://macpup.org/](http://macpup.org/)

Is a Linux operating system on USB (Linux puppy) and it works fine no drive required 
I use this on acer net book which has a dead drive.

You can take the USB with you and use on other computers as long as they can boot from USB in bios or boot option at startup.  Have used on work computer and it made xp look very slow.

Linux puppy is probably the best idea and very fast and will work  on 1gb USB sticks but If you want loads of storage use a bigger stick.

No drivers needed everything just works.

No point reinventing the wheel.  It's already been done.

---

### Post by C.S.Cameron on 2012-07-26
You can install to USB same as to internal drives, you need a minimum 8GB drive for 12.04.
I would suggest unplugging your internal drive while installing on the flash.

---

### Post by oldfred on 2012-07-26
I often post this thread. :)

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I have a full install of Ubuntu 12.04 64 bit more for testing. A bit slow on loading some apps, but functional. As mentioned above a lighter weight version may be speeder. Puppy runs entirely in RAM, but once applications are loaded most Linux runs from RAM. So if you have a lot of RAM it will be faster once loaded even with larger applications.

Also:
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

---

