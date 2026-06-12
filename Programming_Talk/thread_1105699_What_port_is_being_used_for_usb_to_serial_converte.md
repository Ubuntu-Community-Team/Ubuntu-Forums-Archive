---
title: "What port is being used for usb to serial converter"
date: 2009-03-25
forum: Programming Talk
---

### Post by e^(i*pi) on 2009-03-25
I am attempting to use a Python library to control an external device.  The device was designed to plug into a serial port, and the Python script assumes that it is plugged into a serial port.  Since my computer does not have a serial port, I am using a usb->serial adapter.  Whenever I call the Python functions I need to pass as a parameter the serial port the device is hooked up to.  How can I figure out what I should be passing as to the function?  Any advice will be greatly appreciated.

---

### Post by digital_x on 2009-03-25
When you plug in the device use the command dmesg.  It should tell you what the device it gets registered to.  So look for something that starts with /dev/tty (should be something like /dev/ttyS0 or /dev/ttyUSB0).

---

### Post by e^(i*pi) on 2009-03-25
You are correct indeed.  I actually figured it out just a minute ago by installing the gnome-device-manager package and looking at the properties for the device (it was /dev/ttyUSB0).  Thanks for the response, it is greatly appreciated.  Proof again that this is an excellent community.

---

