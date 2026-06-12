---
title: "Access serial port over Bluetooth"
date: 2009-02-17
forum: Programming Talk
---

### Post by Jaykob on 2009-02-17
I don't know if this is the right category here but I didn't find anything better for my question.

I need to access a serial USB GPS device connected to one netbook from another netbook over Bluetooth. Both netbooks are running Ubuntu 8.04 (Ubuntu eee).
The GPS device opens a RS-232 connection via USB and appears as /dev/ttyACM0. Now I want to connect to that device from another netbook, ideally using it as it was plugged in directly.
I searched a lot on google and only found programs that do the same but over TCP/IP.

Is there anything out that I could use? If not how could I implement it by myself in C / C++?

Thanks in advance!
Jakob

---

### Post by Jaykob on 2009-02-17
I just wanted to add that I can't use gpsd because it works with NMEA but I need to work with the U-Blox protocol of the receiver because I need the raw data which is not available in NMEA.

---

### Post by Zugzwang on 2009-02-17
Looks like you want something like this:

[http://en.wikipedia.org/wiki/COM_port_redirector](http://en.wikipedia.org/wiki/COM_port_redirector)

Have a look at the links provided there!

---

### Post by Jaykob on 2009-02-23
Ok, so I first have to establish a RFCOMM connection between the two netbooks and then use one of the programs listed in the link, for example socat, to connect the GPS device to the RFCOMM port?
I'm trying to establish that RFCOMM connection but when it comes to the serial port profile I'm not getting any further. I can add the serial service with [PHP]sdptool add SP[/PHP] but I get a connection refused when I try to connect to that SP because there's nothing behind it, just the service entry is there, right?
I've read something about rfcomm_sppd but in which package is it included?

---

