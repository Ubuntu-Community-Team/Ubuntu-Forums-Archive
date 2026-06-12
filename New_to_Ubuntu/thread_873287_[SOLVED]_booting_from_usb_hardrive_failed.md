---
title: "[SOLVED] booting from usb hardrive failed"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-28
i decided to try installing xubuntu on my usb hardrive,i then re installed ubuntu,and when asked where i wanted to boot from i chose master boot record
well the screen comes up with my choices to boot but when i choose the external hardrive i get an error message:error 21selected disk does not exist.i know perfectly well that xubuntu is installed what can i do to access it?????
rick

---

### Post by rixtr66 on 2008-07-28
how do i change the grub bootloader to boot from a usb device?

---

### Post by kennedy7 on 2008-07-28
I don't know. But they have a grub boot-loader Cd. Just type in grub cd, on google. hey here is a post just change all the hd,0 and stuff to sdb,0. that might work.[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by NewDisciple on 2008-07-28
It has been a while since I did this, but, I believe grub has to on the device you are trying to boot from.  Followed with an edit to fstab.  You didn't say how you installed so I have no idea what steps you took or what tutorial you followed, etc.  Also, you did not say if you altered your bios to boot from a usb device.  If it is a grub issue, there are numerous howto's here on the forum or Google it.

---

