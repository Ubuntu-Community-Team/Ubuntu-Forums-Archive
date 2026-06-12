---
title: "Linux Driver Development"
date: 2007-07-22
forum: Programming Talk
---

### Post by anroy on 2007-07-22
I want to study the development of drivers on Linux.  Very hardcore stuff.  

The work has little to do with Ubuntu but it is my preferred platform as a workstation... and this is a nice forum.  :)

I found a great book, or rather the ONLY book, on the topic here.
[http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

Does anyone know if there exist simple inexpensive hardware dummy devices to test input to and output from serial ports and parallel ports?

I have heard of something called *breakout boards* but was not really able to understand what they do.  Would these be what I want?

How about dummy devices for USB or LAN?

Thanks!

---

### Post by ddrichardson on 2007-07-22
Breakout boxes allow you to isolate components and the computer itself from the power supply - there is no real reason why you can't just solder components onto a connector then plug in and send bits to it to activate, but it normally requires some understanding of microcode.

Maplins sells [something]("http://www.maplin.co.uk/Module.aspx?TabID=1&ModuleNo=42857&doy=22m7") that may be just what you're looking for and £30 is quite reasonable.

---

### Post by slavik on 2007-07-22
find a spare mouse :)

---

### Post by meatpan on 2007-07-22
I'm not sure about parallel and serial ports, but there are a lot of great tutorials for creating drivers with usb ports.  

Linux journal had a great walk-through a few years ago for creating a driver for a usb lantern: [http://www.linuxjournal.com/article/7353](http://www.linuxjournal.com/article/7353)
I think the usb lantern was around $30.

Here is a linux USB device programming guide from the University of Munich: [http://www.lrr.in.tum.de/Par/arch/usb/usbdoc/](http://www.lrr.in.tum.de/Par/arch/usb/usbdoc/)

I recommend going with the guide and buying a fun little usb toy (thinkgeek.com has some great stuff, like usb missle launchers and snowmen).  

Let us know how it goes.  There are quite a few linux device-driver enthusiasts.  I've been working on a USB LED panel w/controller buttons for several years now.  It's a blast to make it work.

---

### Post by geraldm on 2007-07-22
Most electronic stores should have breakout boxes for serial devices.
Radio Shack has had RS232 breakout boxes for years.
They allow access to each signal line, sometimes adding an LED for viewing.
Parallel breakouts are harder to find, probably because they tend to be customized to an
individual's use.  "Parallel Ports Complete", a book by Jan Axelson goes into development
of do-it-yourself interfaces for the parallel port.

The linux kernel contains drivers which are useful examples of how to do it.
For usb devices there is a skeleton driver in drivers/usb/usbskeleton.c which serves the
purpose of being a very generic driver made available for developer's customization.

LAN hardware for tinkering is hard-to-find, probably due to cheap network devices 
like routers and switches.  Microcontrollers can interface to LAN lines, so good sources
are electronic magazines, microcontroller vendors sites.

Gerald

---

