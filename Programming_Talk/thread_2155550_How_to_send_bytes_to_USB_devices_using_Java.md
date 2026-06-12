---
title: "How to send bytes to USB devices using Java?"
date: 2013-06-18
forum: Programming Talk
---

### Post by llleclerc on 2013-06-18
Hi,

I have been searching a lot for a way to write to USB devices in java, but all I find are old projects and use the old usbfs way to represent usb device.
So far I can read from usb devices with jinput.jar which use the /dev/input/eventXX

What I am trying to do should be simple, sending a byte array to the device, does linux propose some way to write to usb device that is accessible through java ?
Is it a must to go through JNI with C projects ?

What do I need to acheive this ?


Thank you VERY much for any hints !


note: I am using ubuntu 12.10, but I can go back to 12.04 if needed.

---

### Post by papibe on 2013-06-18
Thread moved to **Programming Talk**.

---

### Post by Leuchten on 2013-06-19
If you need bindings to C libraries, you can use JNA to write them in java. There is also a project called JNAErator that will generate the java code bindings for a library you point it at.

[https://code.google.com/p/jnaerator/](https://code.google.com/p/jnaerator/)

edit: libusb seems to be the standard way of doing this. It's a C library so it should be pretty easy to have jnaerator generate java binding for it for you.

---

### Post by llleclerc on 2013-06-21
Thank you, in the end, my device had the ability to go in a mode that allowed to see it as a ttyACM0, which I can ln -s to ttyS80 for it to be discovered by rxtx and use mina-serial-transport.

---

