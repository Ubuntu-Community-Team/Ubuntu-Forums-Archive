---
title: "getting data from usb in ubuntu"
date: 2010-05-17
forum: Programming Talk
---

### Post by 234pramod on 2010-05-17
Hi,
I want to receive data which a device which is sending on usb.
How can I receive data.Will there be any C codes available for that?
I am very new to device programming.All suggestion are welcome.??
I want how to interface it and get the data.I want to do this in linux.Finally i want 
to send this through terminal program to other computer in real time.
I have written C program to send data to other comp by reading data from file.I want to 
read from usb instead of file.
If would be great if u can direct me links which direct me regarding usb drivers in ubuntu
Thanks in advance
Pramod

---

### Post by soltanis on 2010-05-17
You can try to communicate with the device using the usbserial module which will attempt to map a file in user land which your program can open and interface with the device in. See
[http://www.linuxjournal.com/article/6573](http://www.linuxjournal.com/article/6573)

But this doesn't always work. It depends on what kind of device it is.

---

### Post by Zugzwang on 2010-05-18
Here's something about writing new Linux USB drivers, which will probably help you (even if you don't intend to write one): [http://matthias.vallentin.cc/2007/04/writing-a-linux-kernel-driver-for-an-unknown-usb-device/](http://matthias.vallentin.cc/2007/04/writing-a-linux-kernel-driver-for-an-unknown-usb-device/)

---

### Post by the_unforgiven on 2010-05-18
> **Zugzwang said:**
> Here's something about writing new Linux USB drivers, which will probably help you (even if you don't intend to write one): [http://matthias.vallentin.cc/2007/04/writing-a-linux-kernel-driver-for-an-unknown-usb-device/](http://matthias.vallentin.cc/2007/04/writing-a-linux-kernel-driver-for-an-unknown-usb-device/)

You generally don't need to write kernel-space USB drivers.
You can use [libusb]("http://www.libusb.org/") from userspace to access the USB device(s).
It even has python bindings :) - [pyusb]("http://sourceforge.net/apps/mediawiki/pyusb/index.php?title=Main_Page").

---

### Post by Zugzwang on 2010-05-18
> **the_unforgiven said:**
> You generally don't need to write kernel-space USB drivers.
You can use [libusb]("http://www.libusb.org/") from userspace to access the USB device(s).
It even has python bindings :) - [pyusb]("http://sourceforge.net/apps/mediawiki/pyusb/index.php?title=Main_Page").

Good point. As there seems to be at least one tutorial on this ([http://www.algorithm-forge.com/techblog/2009/12/using-libusb-to-write-a-linux-usb-driver-for-the-arexx-tl-500-part-i/](http://www.algorithm-forge.com/techblog/2009/12/using-libusb-to-write-a-linux-usb-driver-for-the-arexx-tl-500-part-i/)), this might be the better way to go.

---

### Post by 234pramod on 2010-06-10
Thanks all......

---

### Post by angad on 2011-06-15
hi to all
i m new to linux 
i want to recieve data from the usb and store it in hard disk 
is there any code available to do so 
thanxx

---

