---
title: "How do I show the GRUB menu in GRUB 2"
date: 2013-10-07
forum: New to Ubuntu
---

### Post by NAprMzQ on 2013-10-07
Hi

My GRUB menu is hidden. How do I show it during the boot process? I'm running 13.10 64bit Ubuntu desktop.

---

### Post by heir4c on 2013-10-07
Normally is the 'shift' button you must use to see the Grub menu. After the BIOS screen you press the shift button in.
(The Grub will be only visible if you have more Operating System on your computer.)

---

### Post by heir4c on 2013-10-07
I find something you can change the configuration so you can see Grub every time you boot up:
[http://ubuntuforums.org/showthread.php?t=2130098&p=12577595#post12577595](http://ubuntuforums.org/showthread.php?t=2130098&p=12577595#post12577595)
Or the next post in that thread:
[http://ubuntuforums.org/showthread.php?t=2130098&p=12577790#post12577790](http://ubuntuforums.org/showthread.php?t=2130098&p=12577790#post12577790)

---

### Post by Dennis N on 2013-10-07
Edit the file **/etc/default/grub**

Change **GRUB_TIMEOUT=10** to **GRUB_TIMEOUT=-1**

Then the system will always display the grub menu and stop and wait for you to make a choice, even if there is only one operating system installed.

---

### Post by DuckHook on 2013-10-07
You must run:```
sudo update-grub
```...afterwards to actually commit the change to GRUB.

---

### Post by Dennis N on 2013-10-07
Yes, **/etc/default/grub** is not read during the boot process, but is only used in constructing the generated file **grub.cfg** which IS read during boot-up. Any changes to the former require update-grub to rebuild the latter before they will take effect on boot-up.

grub.cfg = /boot/grub/grub.cfg

---

