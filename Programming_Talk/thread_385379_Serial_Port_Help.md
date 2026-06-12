---
title: "Serial Port Help"
date: 2007-03-15
forum: Programming Talk
---

### Post by vtec on 2007-03-15
I have a gps that connects to a USB port and creates a serial over USB connection. The configuration software is windows only. I have been playing with portmon capturing data, and have so far been able to emulate some of the configurations. According to portmon the windows software sends a:

IOCTL_SERIAL_PURGE	 SUCCESS	Purge: TXABORT TXCLEAR

right before it sends a command. It looks like its clearing the buffers before it writes. In my linux software i just send the command. It seems to work about 30% of the time. My problem is that I'm new to serial port communication and don't understand what a IOCTL_SERIAL_PURGE is. All the examples of stuff I find online seem to be just reading and writing. I can do that fine. Can anyone point me in the right direction????

---

### Post by Mr. C. on 2007-03-15
Each piece of hardware has its own protocols, and each device driver provides some set of ioctl's to control that hardware.  Some are ubiquitous, other's specific to the hardware or hardware class.

To interface with the hardware, you must learn how the hardware works, its protocols, and interfaces.  One way to learn this is as you are doing - a black box, where you intercept the communications and try to reverse engineer what is happening.

Another way is to begin reading references manuals and/or the device driver code.

It appears your serial device requires purging any data on the line before sending a command - but you already know this.  Now, carry it to the next level.

MrC

---

