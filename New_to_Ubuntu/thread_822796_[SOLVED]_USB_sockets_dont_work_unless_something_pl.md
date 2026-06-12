---
title: "[SOLVED] USB sockets dont work unless something plugged in at boot time"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by PetePete on 2008-06-08
My USB sockets only work if there is a device plugged in when the computer first boots.

Strange thing is that the device gets power but /var/log/syslog shows nothing.

Thanks

---

### Post by sithpigeon on 2008-06-08
If your computer is kind of old check your BIOS for a setting about USB and make sure it's enabled. Also make sure your motherboard jumper for usb is enabled.

---

### Post by kansasnoob on 2008-06-08
Installing usbmount from synaptic solved my hot-plugging problems.

---

### Post by PetePete on 2008-06-08
usb worked fine in Fiesty, and its not just storage devices, things like usb speakers and usb mouse don't do anything.

---

