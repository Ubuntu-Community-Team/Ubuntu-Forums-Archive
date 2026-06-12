---
title: "Grub on Usb"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by skyline131313 on 2013-09-22
I need a bootloader to be put on a usb stick, such that the bootloader scans my drives and lists all possible boots possibilities. I screwed up the boot on one of my drives and I am booting it by using grub on another one of my drives but I need to reformat that drive and I can't find a way to get grub on my USB using windows.

---

### Post by david98 on 2013-09-22
It's been a while since i installed grub on a usb but here's a link you may find useful [http://www.porteus.org/tutorials/37-installing/71-install-grub-to-usb-drive.html](http://www.porteus.org/tutorials/37-installing/71-install-grub-to-usb-drive.html) hope this help's you

---

### Post by skyline131313 on 2013-09-22
Only problem is I'm stuck on a windows machine :x.

---

### Post by VMC on 2013-09-22
I just did a simple ```
sudo grub-install --recheck --root-directory=/media/<usb.mount.point>  /dev/sdd
```
Then I copied my grub.cfg file over to the usb stick. The same one as on my hard drive. Works as expected. It comes in very handy.

---

### Post by oldfred on 2013-09-23
I do like VMC, but think you have to have a system with grub installed.

Can you install Supergrub? 
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download the ISO and use unetbootin or pendrive installer?

---

