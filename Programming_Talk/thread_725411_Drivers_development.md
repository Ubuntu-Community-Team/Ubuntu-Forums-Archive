---
title: "Drivers development"
date: 2008-03-15
forum: Programming Talk
---

### Post by StOoZ on 2008-03-15
well im not planing on that, im still on the 'hello world' in c++.
but I was just wondering, for those who do have some knowledge in this field, in order to develop a linux driver for some external device that uses a usb port , do you need to have schemes of how the device is built etc ??
except from a very in depth knowledge in C++ ( or C?) what is needed in order to develop linux drivers??

---

### Post by ruy_lopez on 2008-03-15
The device schematic isn't as important as how the device presents/receives data.

Googling "writing USB drivers":

[http://www.linuxjournal.com/article/7353]("http://www.linuxjournal.com/article/7353")
[http://www.linuxjournal.com/article/4786]("http://www.linuxjournal.com/article/4786")

You can also use [libusb]("http://libusb.wiki.sourceforge.net/"). Libusb is a userland library, so you don't have to mess around at the kernel level.

---

### Post by nick_h on 2008-03-15
Try reading the [Linux Device Drivers](http://www.oreilly.com/catalog/linuxdrive3/book/index.csp) online book on the O'Reilly website.

---

### Post by StOoZ on 2008-03-15
Thanks.
I see that all is in C (according to the provided sources...in this thread), no driver development in C++?

---

### Post by KaeseEs on 2008-03-15
> **StOoZ said:**
> I see that all is in C (according to the provided sources...in this thread), no driver development in C++?

Generally, yes.  You can call C code from C++ pretty well with a simple ```
extern "C" ...
```...but calling C++ code in a kernel module from a C kernel is much more hassle than it's worth.

---

### Post by Ozitraveller on 2008-03-15
Also I read somewhere recently about (I think) Novel or maybe IBM working towards having the device driver bits outside of the kernel.

---

### Post by Fbot1 on 2008-03-15
> **StOoZ said:**
> But I was just wondering, for those who do have some knowledge in this field, in order to develop a linux driver for some external device that uses a usb port , do you need to have schemes of how the device is built etc ??
You mean like a drawing?
> **StOoZ said:**
> except from a very in depth knowledge in C++ ( or C?) what is needed in order to develop linux drivers??
You need to understand linux's driver API.

---

### Post by supirman on 2008-03-16
You need to be familiar with the kernel APIs as well as how the device communicates.  If it's a device that is memory mapped, you'll need to know the register set it exposes as well as all of the register functions (control registers, status registers, read/write registers, etc).  If it's a device which is communicated with over a bus, you need to know what the communication scheme is.  Example buses would be spi, i2c, usb, etc.  You then need to understand both the bus, and also the available communication API for the device itself.  Schematics really aren't needed for drivers, just the communication interface is needed.

---

