---
title: "usbserial problem"
date: 2010-05-12
forum: Programming Talk
---

### Post by seheatwole on 2010-05-12
I am trying to set up a novatel gps receiver to work in Ubuntu 8.04 using the usbserial driver.  I have have the vendor id and product id and am using the commands :
 mknod /dev/ttyUSB0 c 188 0
sudo modprobe usbserial vendor=#### product=####

to set up the usb port on ttyUSB0

This works fairly well and I can communicate with the device via hyperterminal and can see ASCII messages come over.  When I switch to have binary messages sent, I see that 0x13 is stripped from the message.  The software version number is in every header and it has 0x13 in it which does not show up in the output of the port.  Every message comes out 1 byte shorter than it should be.

 I verified that the receiver was outputting the message correctly on a windows machine and saw the 0x13 byte where it should be.  

Looking at the ASCII tables, 0x13 is a hardware control XOFF byte.  Are there any settings in the usbserial driver that I can toggle to prevent it from stripping this byte out?

---

### Post by soltanis on 2010-05-12
I think that to solve the problem, you need to set the flow control on the port to "none" (vs Xon/Xoff). I personally don't know the command for setting that on the serial port, though.

---

### Post by sprince09 on 2010-05-12
Here are the references I usually use for serial port IO in Linux:

[http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html](http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html)
[http://www.faqs.org/docs/Linux-HOWTO/Serial-Programming-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Serial-Programming-HOWTO.html)
[www.linux.org/docs/ldp/howto/Serial-HOWTO-11.html](www.linux.org/docs/ldp/howto/Serial-HOWTO-11.html)

---

### Post by seheatwole on 2010-05-13
It is a usbserial problem.

 I verified the problem by creating a program to output characters 0-255 out over the serial port from another computer and read it through the serial and virtual USB serial ports via a generic serial to usb converter.  The serial port read every character but the usbserial driver removed 0x13 when reading over the USB using the same settings to open and read the port.  

I was able to get access to a box with Ubuntu 9.10 on it and the problem did not show up which makes me believe that the problem was fixed in the kernel driver between 8.04 and 9.10.

I guess I will go and upgrade to 10.04 now.

---

### Post by not_a_phd on 2010-05-16
Good thing you posted on this forum. Don't know what you would have done without the quality advice. Recommend you mark the post as [SOLVED]. I think only you can do it. 

For anyone else attracted to the Siren call of the generic usbserial kernel module to communicate with a device (like the Novatel GPS receiver) that sets up multiple virtual serial ports accessible on a single USB physical connection - take heed: The usbserial kernel module is deceptively simple and useful, but it is also somewhat hosed. A casual inspection of the the code reveals a patchwork of workarounds for current and former bugs that might make the figurative one-armed paper hanger take the time from his frenetic hanging and gluing to tip his hat.  

The author of this thread appears to have found temporary harbor from his mysterious binary data corruption with an updated kernel, but I would suspect that he is likely one or two kernel updates away from data port disaster. This is unfortunate, because I know of no other OS that offers such a generic facility for giving the user access to the USB port as a generic serial device.

---

