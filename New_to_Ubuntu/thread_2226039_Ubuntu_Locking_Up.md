---
title: "Ubuntu Locking Up"
date: 2014-05-24
forum: New to Ubuntu
---

### Post by perpetuum_mobile2 on 2014-05-24
My Ubuntu 12.04 frequently locks up. The frequency of lockups varie between once in 3 days to 5 times in an hour. Usually while using Gimp, but randomly with any other programs.
The only consistency in the lock ups is that they happen while switching windows, one window is fading out half way and the other is fading in half way. The system has 2G Ram and 3.0 GHz processor.
Any ideas of the cause?
Step 1. Is there a way to disable fade-ins/fade-outs?

---

### Post by whitesmith on 2014-05-24
Flaky hardware is suggested by stochastic behavior of your system. Try running mem86 overnight and see if errors are noted. Regards.

---

### Post by perpetuum_mobile2 on 2014-05-25
I am trying to setup mem86 to run from a flash drive. It came with the following instructions:
"Instructions for creating a bootable MemTest86 USB drive. For Linux:
1) Insert a USB drive into a USB slot.
2) Determine which device the USB drive is assigned as (eg. /dev/sdc).
3) As root type the following command: 
dd if=memtest86-usb.img of=dev
where dev is the device the USB key is assigned to. Use the base device (ie. /dev/sdc) not a partition designation (ie. /dev/sdc1)."
------------
After typing in:
user@user-desktop:~$ dd if=/home/user/Downloads/mem86/memtest86-usb.img of=/dev/sdb
I received the following error message:
dd: opening `/dev/sdb': Permission denied
What am I doing wrong?

---

### Post by staticn0de on 2014-05-25
You need to run the command as root so use sudo. 

Also, make sure sdb is your thumb drive.

---

### Post by tgalati4 on 2014-05-26
Memtest should already be installed.  Hit *esc* during boot to bring up the GRUB menu and select it there.  Your graphics card could be failing.  It happens.  Is this a desktop or laptop?  If this is a desktop, try cleaning the machine and reseating the graphics card.  If this is a laptop, there is not much you can do.  Search for your model on the web and see if others are having problems.

---

