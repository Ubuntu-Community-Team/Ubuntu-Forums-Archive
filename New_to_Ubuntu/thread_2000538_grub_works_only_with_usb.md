---
title: "grub works only with usb"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by nikhilb020875 on 2012-06-09
I made a USB bootable Ubuntu 12.04 on my pen drive for installing the OS on my system. I have installed and it started working. But the problem is every time I need to work on linux i have to connect my pen drive and boot it via usb. Or else its not showing the grub menu and simply hangs.


I ran  bootinfoscript. Result file is attached with the post. Any help would be appreciated.


Regards,
Nikhil

---

### Post by wilee-nilee on 2012-06-09
You actually have grub in the HD's mbr but do this, boot to the installed ubuntu and remove the usb stick and run these commands.
```

sudo grub-install /dev/sda
```
then
```
 sudo update-grub
```

you should boot straight in now without the stick.

---

### Post by nikhilb020875 on 2012-06-09
That solved my problem.
Thanks !!

---

### Post by wilee-nilee on 2012-06-09
> **nikhilb020875 said:**
> That solved my problem.
Thanks !!

No problem, enjoy. ;)

---

