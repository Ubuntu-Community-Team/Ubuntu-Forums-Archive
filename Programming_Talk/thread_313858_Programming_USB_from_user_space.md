---
title: "Programming USB from user space"
date: 2006-12-06
forum: Programming Talk
---

### Post by funnyfraggle on 2006-12-06
I am trying to write a library for my company's USB products that enables users to write code for their own needs.

I'm using libusb.

I can find the device and open it with usb_open, but when I try to send a control message I always get a return of -1 from usb_control_msg.

I have tried claiming the interface, but that always fails. So does trying to set the configuration. 

Our USB boards only use control messages, and when I wrote the libraries for MAC OS X and Windows I only had to open the device. There was no need to claim an interface, etc.

Strangely enough, when I try to run my test program with sudo I get random garbage for data, but no error returns from the functions.

Can anyone point me to a sample that does a simple open and control message to a USB device? Any help would be greatly appreciated.

---

