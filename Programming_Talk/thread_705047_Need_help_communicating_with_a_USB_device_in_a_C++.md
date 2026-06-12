---
title: "Need help communicating with a USB device in a C++ program"
date: 2008-02-22
forum: Programming Talk
---

### Post by robotool on 2008-02-22
Hey all,

I recently purchased a USB device that I'd like to use in a robotics project that I'm working on.  However, the company that makes it does not have device drivers for Linux, and I need to be able to read information from the device from within a program that I'm writing.  I have the technical specifications for the device that describe how to interpret the data that the device sends back.  I'm a pretty good programmer in C++, and I can get around the Linux operating environment pretty well, but this is the first time I've needed to communicate with a USB device in a program that I've written.

Can anyone help me get started with this?  Is there a simple tutorial online somewhere that's good for someone who has no experience yet interfacing with usb devices?

---

### Post by ryanhaigh on 2008-02-23
Depending on the device you may actually find that it uses a virtual serial port for communication rather than 'proper' usb. When you plug the device in check the output of dmesg and msee if there are any /dev/ttyUSB# devices. If this is in fact the case for your device you can simply use serial comms to talk to your device and there should be plenty of info available about doing so in C++ (I have only really done it in Python). If you do have to use the USB protocol then you may want to look at libusb [http://libusb.wiki.sourceforge.net/](http://libusb.wiki.sourceforge.net/)

---

