---
title: "USB to RS232"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by barrykgerdes on 2012-07-12
I have two USB-232 converters that I can connect to an ACER 5560 running 11.04. Note: these converters are probably clones

lsusb shows that they available as Prolific Technology, Inc PL2303 Serial Port

dmesg shows that they are recognised as dev/ttyS0

When I use Stellarium and try to connect the telescope as dev/ttyS0 the program locks up and needs a forced kill to get out

The same program on another computer (also 11.04) but having a real COM1 (dev/ttyS0) port controls the telescope without bother.

 However if I add the same converter it is recogised as a PL2303 again but is now connected as dev/ttyUSB0

Stellarium now locks up as on the other computer

The Stellarium connection requires 9600 8 N 1. could this have anything to do with it or is it that the adapters are not true pl2303.

Barry

---

### Post by barrykgerdes on 2012-07-18
With no suggestions I have solved this problem myself by purchasing a Belkin F5U109 serial adapter. This worked as soon as it was plugged in.

Barry

---

