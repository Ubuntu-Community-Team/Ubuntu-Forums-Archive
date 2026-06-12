---
title: "Device USB (uhci_hcd)"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by oscarvady on 2013-05-06
Hello everybody,

I connected a USB Device and if I do **dmesg** apeear:[INDENT][I]usb 2-2.1: new full-speed USB device number 11 using uhci_hcd
[/I][/INDENT]


**lsusb**[INDENT]Bus 002 Device 011: ID 1366:0101 SEGGER J-Link ARM[/INDENT]



I need see this device on **/dev** directory for a flasher application


Thanks in advance,
Oscar

---

### Post by ikt on 2013-05-06
Technically it should already be in /dev.

Are you able to find the device if you do:

sudo fdisk -l

---

