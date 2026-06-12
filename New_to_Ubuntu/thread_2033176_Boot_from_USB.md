---
title: "Boot from USB"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by Beengt on 2012-07-25
so, I installed ubuntu 12.04 via a USB.
I couldnt boot ubuntu if I hadnt the USB plugged in.

First of all:
how do I fix this? 
(ive read alot of guides etc to fix this but nothing works)

Second of all:
ive lost the USB-stick and now i cant boot my computer -.-
I did purchase a new usb-stick and made it 
bootable with "Pen Drive Linux's USB Installer" (as I did last time).
And now when I boot the computer with the stick in it just asks me if I want to reistall ubuntu.

So here's my question:
Where can I find this specific boot file?

*i can make due to always have the USB plugged in... i just want to use my laptop again.

thanks alot

---

### Post by Basher101 on 2012-07-25
Looks like you installed grub on the USB instead of your HDD. You can try to fix it running this [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) with a Live boot session. As for Reinstall, there should also be the option "Other" below it. You can use that to make a custom install. You should make sure that you are able to manually set the partitions if you choose this.

regards

---

