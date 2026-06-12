---
title: "Obtaining Low Level Access to a USB Port"
date: 2011-05-23
forum: Programming Talk
---

### Post by MetalheadGautham on 2011-05-23
Hi!

I'm starting to learn embedded programming with microcontrollers. I've a few projects in mind which involve stuff where the controller is interfaced to my laptop via a USB port and accepts inputs via the USB interface and also gives some outputs to the system.

Trouble is I have honestly no idea how a USB port can be accessed at the low level in Linux, where I can program an application to take complete control of the port. I'm looking for ways to do this. I program mostly in C++ but I'll soon start learning python. So can someone point me to resources that can help me ?

---

### Post by Zugzwang on 2011-05-23
There are some links to very helpful web pages in another thread: [http://ubuntuforums.org/showthread.php?t=1486025&highlight=USB](http://ubuntuforums.org/showthread.php?t=1486025&highlight=USB)

Make sure to read all of the posts before following the links.

---

### Post by krazyd on 2011-05-23
yep, try [http://www.libusb.org/wiki/libusb-1.0](http://www.libusb.org/wiki/libusb-1.0)

---

### Post by cszikszoy on 2011-05-23
Easiest thing to do would be to use a USB to RS232 converter cable.  It will show up on the host computer as a regular serial port (/dev/ttyUSB0, probably).  Almost all micro controllers have a hardware uart so it's trivial to read rs232 serial data with them.

The benefit of this approach is that it's very easy to open and write data to a serial port, compared to writing data to a USB device.  You are obviously more limited as USB has a much higher bandwidth, but most uC's can do 115200 baud even with the built in RC oscillators.

---

### Post by MetalheadGautham on 2011-05-23
> **cszikszoy said:**
> Easiest thing to do would be to use a USB to RS232 converter cable.  It will show up on the host computer as a regular serial port (/dev/ttyUSB0, probably).  Almost all micro controllers have a hardware uart so it's trivial to read rs232 serial data with them.

The benefit of this approach is that it's very easy to open and write data to a serial port, compared to writing data to a USB device.  You are obviously more limited as USB has a much higher bandwidth, but most uC's can do 115200 baud even with the built in RC oscillators.

Are you talking about ease of write from the PC or from the uC ?
Because its the PC Interface I'm worried about since a PIC18F course I'm attending sort of covers everything from the uC point of view.

And can the uC be powered using the USB port or Converted Serial Port ?

---

### Post by MetalheadGautham on 2011-05-28
I went through all the links available.
There is still no complete beginners libusb-1.0 documentation available. The wiki seems only half done. Can someone point me to the right place to start reading ?

---

### Post by Zugzwang on 2011-05-29
> **MetalheadGautham said:**
> I went through all the links available.
There is still no complete beginners libusb-1.0 documentation available. The wiki seems only half done. Can someone point me to the right place to start reading ?

In the post above I pointed to some other threads where a tutorial link for libusb has been posted. The tutorial itself is relatively compact, but has pointers to other helpful resources. For your convenience, I'm copying the link here: [http://www.algorithm-forge.com/techblog/2009/12/using-libusb-to-write-a-linux-usb-driver-for-the-arexx-tl-500-part-i/](http://www.algorithm-forge.com/techblog/2009/12/using-libusb-to-write-a-linux-usb-driver-for-the-arexx-tl-500-part-i/)

---

