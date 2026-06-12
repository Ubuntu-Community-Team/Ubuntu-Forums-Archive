---
title: "Driver for USB osciloscope"
date: 2010-01-09
forum: Programming Talk
---

### Post by phoenox on 2010-01-09
I have a link instruments DSO 8500 osciloscope that I would like to get working in linux.  Right now I have it working using virtualbox, but this is not ideal.  I am considering writing a driver for it that will control the osciloscope and take the data from it, then send the data to gnuplot to be displayed.

I have some programming experience(mostly in c).  Lately I have been doing a lot of PIC microcontroller programming.  But I have never done anything with USB or taken on a project of this size.  I would be willing to learn a new language if it makes this task easier, but I am really most comfortable programming in C.

I have been in contact with the manufacturer and asked for information about how the data is sent to and from the osciloscope.  I do not know whether they will provide me with this or not.

So I am here today looking for resources, information and pointers to get me going in the right direction.

---

### Post by Zugzwang on 2010-01-10
Here's something about writing new Linux USB drivers: [http://matthias.vallentin.cc/2007/04/writing-a-linux-kernel-driver-for-an-unknown-usb-device/](http://matthias.vallentin.cc/2007/04/writing-a-linux-kernel-driver-for-an-unknown-usb-device/)

---

