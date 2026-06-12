---
title: "USB keyboard Driver"
date: 2016-01-14
forum: New to Ubuntu
---

### Post by RamanKumar on 2016-01-14
Is their any need for including usb_register() and usb_unregister() inside module of USB keyboard driver ?
And what about device files of USB Devices?

---

### Post by Autodave on 2016-01-14
I have never run across any keyboard that just didn't work fine by simply plugging them in.  Are you having trouble getting a keyboard to operate properly?

---

### Post by Mark Phelps on 2016-01-14
The basic functionality of a USB keyboard will work fine, without any special drivers needed.

But, if the keyboard has special functions, like Macro keys on Gaming keyboards, those require special software -- and that is nearly always available only for MS Windows.

---

