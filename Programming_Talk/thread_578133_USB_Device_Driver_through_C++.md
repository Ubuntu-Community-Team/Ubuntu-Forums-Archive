---
title: "USB Device Driver through C++ ?"
date: 2007-10-16
forum: Programming Talk
---

### Post by Pashton on 2007-10-16
Hello,
I was wondering if any of you have ever tried this, basically my aim is to write out to a USB powered motor from linux; then i can expand from there on. 
Now of my expereince, i can programme in C++, can work my way around in SHELL, i have did a little bit of googling but nothing is straightforward. In simple words, what all do i need; any additional learning, C per say? how can i go about making the Driver for this DC motor powered through the USB, how can i send the signal though the USB port to run this motor.
Thanks for the prompt reply,
Pashton

---

### Post by j_g on 2007-10-17
You may want to investigate the libusb shared library. ([http://libusb.sourceforge.net](http://libusb.sourceforge.net)) This library is intended for apps to access/control USB devices. Sometimes, you can write a service which uses libusb in lieu of actually writing a device driver. So, you could write your service in C++.

Otherwise, if you decide to write an actual device driver, I'm not certain if you can do it in C++. You can't call the C library functions (and lots of the C++ paradigms are interfaces to that, such as cout being an interface to printf). Those are meant to be called from "user space" whereas a device driver runs in "kernel space" and therefore must call only those APIs which are for "ring 0 code" (kernel space). That's why most drivers are written in C, with linker flags that omit some user space startup code, and the C driver eschews any calls to C lib functions and instead calls the API for drivers.

---

