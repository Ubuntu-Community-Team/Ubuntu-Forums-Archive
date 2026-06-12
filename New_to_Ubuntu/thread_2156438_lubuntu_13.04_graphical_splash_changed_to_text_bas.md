---
title: "lubuntu 13.04 graphical splash changed to text based"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by opfeld on 2013-06-21
I didn't, purposely, do anything to alter the boot screen in my lubuntu 13.04 install, but the nice graphical splash screen has changed to a text based one.  Any suggestions on changing it back?

---

### Post by 2F4U on 2013-06-22
Maybe the splash screen has been disabled. Check /etc/default/grub. This post shows how to disable splash, so you would have to reverse the instructions:

[http://askubuntu.com/questions/129738/can-i-disable-the-ubuntu-splashscreen](http://askubuntu.com/questions/129738/can-i-disable-the-ubuntu-splashscreen)

---

### Post by Rebelli0us on 2013-06-22
In /etc/default/grub try:

GRUB_CMDLINE_LINUX="splash quiet vga=794"

---

