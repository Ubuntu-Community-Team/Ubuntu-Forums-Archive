---
title: "[SOLVED] I am using a VM called Virtual Box"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-17
I am using virtual box and installed windows xp pro. I also installed a capture card on the VM. Now here is the problem. I install the driver inside virtual box and when I plug in the capture device it won't recognize it. It says

"There is no capture device installed or plugged into this machine".

Any help

---

### Post by hyper_ch on 2008-07-17
You need to assign it first to the vm. Is it an USB device are pci card?

---

### Post by deadlySniper on 2008-07-17
it is a USB device and I have all the settings turned on that I need

---

### Post by jimmy the saint on 2008-07-19
read the tutorial here
[http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html](http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html)

you need to do a few things in order to enable usb support for virtualbox guests.

---

### Post by adamogardner on 2008-07-19
this helped me through a similar situation:
 [http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

---

