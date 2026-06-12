---
title: "[SOLVED] How to enable usb in VirtualBox"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-01
I can see my IPOD under "Device" in VirtualBox(VB). However, when I try to connect, I get error message as per attachment. I'm still searching for the solution but if anybody already know it, please share with me. I was following [http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html). So far I has edited /etc/init.d/mountdevsubfs.sh.

---

### Post by Elfy on 2008-07-01
There is no attachment.

I followed similar, but alos had to add this to my fstab

none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

where 124 is my vbox usergroup

Did you reboot?

You also have to edit the usb details to add the device, plug it in go to vbox settings - usb - one of the icons on the left of the USB panel allows you to add the usb. Maybe that - although I've never tried with an ipod as I don't have any.

---

### Post by ChameleonDave on 2008-07-01
> **wariskampar said:**
> I can see my IPOD under "Device" in VirtualBox...
I assume that you have installed whatever special software that iPods require for connection, and that you are using the full version of VirtualBox rather than the open-source edition?

Just checking.

---

### Post by bumanie on 2008-07-01
Download the binary version (free 4 home use) and follow this [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

---

### Post by wariskampar on 2008-07-01
Problem solved! Thanks guys. I just need to finish every steps in the link and restart my laptop. forestpixie suggestion are very correct. Thanks again! Now I just need to remove Banshee and re-install RhythmBox.

---

