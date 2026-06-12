---
title: "USB using Pyserial connecting to xbee radio"
date: 2011-12-15
forum: Programming Talk
---

### Post by vornado on 2011-12-15
a problem communicating to ports.  I just solved a similar problem with eclipse and my ATMEL AVRxmega128 a3  but this one has had me going for 2 days.

working in ubuntu 11.10.  using python2.7.2+

please tell me if you need more details.

running from terminal.
trying to open serial port.

Have this at the top of file which main.py calls to

```
# -*- coding: utf-8 -*-

"""
Module implementing MainWindow.
"""

from PyQt4.QtGui import QMainWindow
from PyQt4.QtCore import pyqtSignature

from Ui_control_panel import Ui_MainWindow

import serial
```and this in the code:

ser = serial.Serial('/dev/XBEE', timeout=1, parity=serial.PARITY_NONE, bytesize=serial.EIGHTBITS, stopbits=serial.STOPBITS_ONE)

I have also tried changing /dev/XBEE to usb, usb_device et cetera ad nauseum

when I run as sudo I get this:


Traceback (most recent call last):
  File "/home/user/.../ui/control_panel.py", line 30, in on_openButton_released
    ser = serial.Serial('/dev/XBEE', timeout=1, parity=serial.PARITY_NONE, bytesize=serial.EIGHTBITS, stopbits=serial.STOPBITS_ONE)
  File "/usr/lib/python2.7/dist-packages/serial/serialutil.py", line 260, in __init__
    self.open()
  File "/usr/lib/python2.7/dist-packages/serial/serialposix.py", line 280, in open
    self._reconfigurePort()
  File "/usr/lib/python2.7/dist-packages/serial/serialposix.py", line 308, in _reconfigurePort
    raise SerialException("Could not configure port: %s" % msg)
serial.serialutil.SerialException: Could not configure port: (25, 'Inappropriate ioctl for device')

I have added the Symbolic link in my lib/udev/rules.d as:

#This is the rule for the xbee radio
SYSFS{idVendor}=="0403",SYSFS{idProduct}=="ee18", SYMLINK="XBEE"

I got my numbers from lsusb.

I have edited the permissions in /etc/udev/rules.d as:

# Future etc
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0403", SYSFS{idProduct}=="ee18", MODE="660", GROUP="dialout"

I have tried with usb SUBSYSTEM as well.  
  

when I ls the /dev folder I see my XBEE link and also:
user@host:~$ ls -l /dev/XBEE
lrwxrwxrwx 1 root root 15 2011-12-15 16:54 /dev/XBEE -> bus/usb/003/002

when I mess around with the names of things, sometimes the error message is file or directory not found 

any help, much obliged.

---

### Post by vornado on 2011-12-15
I mean trying to open USB.  not serial.

---

