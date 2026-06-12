---
title: "using &gt;1 USB-Serial Adapter via USB hub -- port names"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by owen.rickards on 2012-04-24
Hi,

So not an absolute beginner, but this is probably the best place. I need to use 2 separate USB-RS232 adapters via an external USB hub. How do I ensure that my software always chooses the correct one of these two ports (dev/ttyUSBx) after e.g. unplugging the USB hub, even rebooting? Or is this a non-issue? 

System is Ubuntu 11.10, the 2 adapters I think are different brands (can't be sure sorry). This will be a semi-permanent setup; the adapters will stay plugged into the USB hub, but said hub may be unplugged from the laptop. I can't seem to find an answer myself.

Thanks in advance for any help.

---

### Post by sanderj on 2012-04-24
Interesting question.

Does [http://askubuntu.com/questions/49910/how-to-distinguish-between-identical-usb-to-serial-adapters-using-udev-rules](http://askubuntu.com/questions/49910/how-to-distinguish-between-identical-usb-to-serial-adapters-using-udev-rules) help?

PS: a "lsusb" will show the USB-id's of the devices ... do they differ?

---

