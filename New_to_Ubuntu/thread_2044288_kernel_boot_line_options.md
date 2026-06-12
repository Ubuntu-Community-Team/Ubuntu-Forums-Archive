---
title: "kernel boot line options"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by takaya on 2012-08-19
hi everyone, 

[LEFT]I am trying to follow a guide posted [http://blog.smalleycreative.com/linux/fix-for-ubuntu-10-04-server-usb-install/](http://blog.smalleycreative.com/linux/fix-for-ubuntu-10-04-server-usb-install/)

I am stuck at part 2.
how do I add the kernel boot line option?

I am trying to install 10.04 server on a dmp keyboard pc as I am led to believe that the r6040 ethernet driver works by default.

[LEFT]I have tried loading the manufacturer's driver on 10.04 desktop, which gives back numerous errors.

I am new to linux so please go easy on me.
any help would be greatly appreciated.

regards
[/LEFT]
[/LEFT]

---

### Post by cwsnyder on 2012-08-19
You add the kernel boot option to the boot line in GRUB.  When you get to the GRUB menu, simply press the E key to edit your menu entry and add the **cdrom-detect/try-usb=true** option to the end of the line which has /boot/vmlinuz at the start of the line. To add this to GRUB for the next boot, simply editing the /etc/default/grub file by ```
sudo nano /etc/default/grub
``` and changing the line GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="cdrom-detect/try-usb=true", then pressing the key combination Ctl-o, press enter when it shows the file name, then press the Ctl-x key combination to exit nano.

---

