---
title: "USB Serial converter"
date: 2017-04-25
forum: New to Ubuntu
---

### Post by northernexposure on 2017-04-25
I am trying to connect with a Future Technology FT232  Serial-USB Converter. Running lsusb shows the converter. Also running dmesg | grep FTDI it shows the USB Serial Device Converter detected and attached to ttyUSB0. I tried to open /dev/ttyUSB0 with pyserial open in python  and tried to connect with tio /dev/ttyUSB0 -b 9600. In the first case, I got no such file or directory /dev/ttyUSB0 and with tio it would not connect. I am using Ubuntu 16.04. I would appreciate any help in getting the USB working.

---

### Post by northernexposure on 2017-04-26
I was able to resolve the problem with the following command:  chmod 777 /dev/ttyUSB0,  Both tio and pyserial were able to access the USB port.

---

### Post by northernexposure on 2017-04-29
Although I was able to open the USB0 port with the chmod command, if I leave the computer for several hours, when I reenter with my password I get the same message of no such directory or file. Using the chmod command again gives me the same message. The only way I can get the chmod 666 /dev/ttyUSB0 to work is to reboot the system. Can anyone tell me if there is a way to not have to reboot?

---

### Post by HermanAB on 2017-04-29
You have to join the dialout group.

A good serial communication program is cutecom and of course the venerable minicom.

---

