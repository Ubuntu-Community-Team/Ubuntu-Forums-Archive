---
title: "Usb2Serial problem"
date: 2010-12-18
forum: Programming Talk
---

### Post by aworld on 2010-12-18
Hi, all

I got a problem with my usb2serial adpater, it can not read or send anything.

First, Details of my laptop:

I have Dell Studio 15, i5 64 bit. But, I have installed 32 bit 10.04 LTS ubuntu.  //** could this be a problem?

Second, my problems:

I have a FTDI usb->serial adapter, I just want to do a simple program which makes it read & write for testing. But, It does not work!!! 

In testing, besides my program, I installed "cutecom", a serial terminal with a GUI interface. I chose "/dev/ttyUSB0" as my device, 8N1,9200 for baudrate..etc I connect this serial port to my win7 64bit desktop, and I configure the COM1 with the same parameters. But no matter what i send, I receive nothing on my Linux side, and no matter what I am trying to send from Linux, I also got nothing on my windows7 screen.... strange....

I also have used a oscilloscope to check the serial port from my win7, It gives me perfect, clean data. (ofc, I connect pin5 as signal ground, and test pin3 as the port for transmitting). When i test my linux serial port, I got something, but the data is ****, looks like a saw teeth all the time, And it seems the data is transmitted 10x faster than windows serial port..... 

More information:

I have checked with command "dmesg | grep usb", it gives me information like "FTDI usb2serial converter has been attached to ttyUSB0".

When using lsusb, i also got the vender ID and product ID.

In order to avoid some permission issue, I run my program and "cutecom" as a root user, but still nothing....

No matter how many bugs my program have, it should at least work with "cutecom", at least show me something on screen, and at least send something readable by another serial terminal..... 

I wont have a nice Chrixmas if I can not solve this problem.... Any advice???

If you need more information, I can post them here.


FYI:

no matter in my program or in some terminal software, I dont have any error message!!!!!!!! No Error at all...............
(If I choose some other device, at least it shows me "opening failed..." or "can not open device" !!!)

for compiling, I am just using gcc...........

---

