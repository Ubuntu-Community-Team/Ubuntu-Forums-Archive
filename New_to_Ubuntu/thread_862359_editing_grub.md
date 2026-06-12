---
title: "editing grub"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by SVWander on 2008-07-17
Each time there is a kernel update on my desktop system a new line is throw into the grub menu. It looks a little like this:
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-18-generic
Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-17-generic
Ubuntu 8.04.1, kernel 2.6.24-17-generic (recover mode)
Ubuntu 8.04.1, kernel 2.6.24-16-generic
Ubuntu 8.04.1, kernel 2.6.24-16-generic (recover mode)
Ubuntu 8.04.1, memtest86+
Other operating systems:
Microsoft Windows XP

Do I really need all those other kernel updates in grub and if not how do I edit them out? Or should I just leave them alone?

Thanks, Tim

---

### Post by Morpheun on 2008-07-17
> **SVWander said:**
> Each time there is a kernel update on my desktop system a new line is throw into the grub menu. It looks a little like this:
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-18-generic
Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-17-generic
Ubuntu 8.04.1, kernel 2.6.24-17-generic (recover mode)
Ubuntu 8.04.1, kernel 2.6.24-16-generic
Ubuntu 8.04.1, kernel 2.6.24-16-generic (recover mode)
Ubuntu 8.04.1, memtest86+
Other operating systems:
Microsoft Windows XP

Do I really need all those other kernel updates in grub and if not how do I edit them out? Or should I just leave them alone?

Thanks, Tim

You usually won't need all of those. Install startup manager  (sudo apt-get startupmanager) and limit it if you want to. (I suggest to 2, just in case a kernel update doesn't work with your system). Just go to the advanced tab and change the "number of kernels to keep".

---

### Post by cdtech on 2008-07-17
It's fine to edit the ones you don't use out of the grub menu list. If you have a kernel that works for you and your happy with it you can uninstall the existing kernels through Synaptic Package Manager if you want.

After you edit the grub file just save and reboot, no need to do update-grub.

---

### Post by chrisod on 2008-07-17
That should be ```
sudo apt-get install startupmanger
```

---

### Post by old_geekster on 2008-07-17
I normally keep at least two kernels in GRUB that work correctly.  This way if one goes bad, I can use the other.

"Startupmanger" works great!

---

### Post by SikEnCide on 2009-03-25
ide rather edit the grub list on my own instead of an app doing it. where is it hidden in ubuntu ?

---

### Post by SikEnCide on 2009-03-25
n/m found it. its  /boot/grub/menu.lst

---

