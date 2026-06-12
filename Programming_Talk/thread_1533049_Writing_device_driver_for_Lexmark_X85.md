---
title: "Writing device driver for Lexmark X85"
date: 2010-07-17
forum: Programming Talk
---

### Post by fernandoc1 on 2010-07-17
I have an old Lexmark X85 printer/scanner, and there is no device driver for it. 
I want to write one. 
My plan is to install the printer in a virtual machine running Windows and analyze the traffic, from Linux, using Wireshark USB capabilities. 
Wireshark is actually capable to get raw USB traffic, direct from USB interface. 
Initially, I want to try a user space driver, using libusb as my layer to communicating with the printer. 
My problem is that I never wrote a device driver, and I need some advice. 
I wanna know how can I extract relevant data from wireshark output and how can I use libusb primitives. 

This is the link where I'm putting the information that I got 
[https://docs.google.com/document/pub?id=1O1c-MAz_UyZLzbhpZxphGUXRsMPYZQp6BHBtmUAw5jk]("https://docs.google.com/document/pub?id=1O1c-MAz_UyZLzbhpZxphGUXRsMPYZQp6BHBtmUAw5jk")

---

### Post by DanielWaterworth on 2010-07-17
Wow, that's quite a difficult task. I'd start with a related driver, chances are there's some similarities.

---

### Post by soltanis on 2010-07-17
Sounds like you have more or less the right idea. Log traffic using Wireshark, dump the data to file, and then try to emulate that using a userspace driver.

A little Googling gave these resources:
[http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0,0](http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0,0)
- On writing drivers, though it discusses kernelspace drivers
[http://libusb.sourceforge.net/api-1.0/](http://libusb.sourceforge.net/api-1.0/)
- The libusb documentation
[http://tldp.org/LDP/khg/HyperNews/get/devices/fake.html](http://tldp.org/LDP/khg/HyperNews/get/devices/fake.html)
- On writing userspace drivers

---

### Post by pbrane on 2010-07-17
You should try to figure out what kind of chip set the printer is using and write the driver based on that. The network sniffing isn't going to give you the details you need to initialize the printer chip set.

---

