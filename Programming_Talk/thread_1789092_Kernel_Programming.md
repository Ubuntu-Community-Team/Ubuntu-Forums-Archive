---
title: "Kernel Programming"
date: 2011-06-23
forum: Programming Talk
---

### Post by jaypatel on 2011-06-23
I am new to kernel programming.I wish to develop a program to read USB drive information like its manufacturer name,capacity,etc.I know about descriptors and their attributes.But I dont understand how to enumerate USB drives connected to the system.I am looking for the function which initiates connection between kernel and USB port.How is it possible?

---

### Post by cgroza on 2011-06-23
The library libusb deals with usb manipulation. I am not sure if it is relevant  to your case though.

---

### Post by jaypatel on 2011-06-23
libusb cannot find drive space,capacity.What I just need is how to initiate connection between kernel and USB devices.

---

### Post by zobayer1 on 2011-06-23
> **jaypatel said:**
> libusb cannot find drive space,capacity.What I just need is how to initiate connection between kernel and USB devices.

You can take a look on /dev and open specific device you want, and then use their properties.
In my system, I can see 4 usb items in /dev. In many system, there are ttyUSB type devices. I am not sure though.

I never used usb port, but once we programmed serial ports, which was ttyS0 ... etc. so, you can do it with some C system calls and library functions.

---

