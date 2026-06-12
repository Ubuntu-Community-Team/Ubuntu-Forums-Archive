---
title: "Serial Monitor"
date: 2007-02-15
forum: Programming Talk
---

### Post by hatchek on 2007-02-15
Hello, I want to write a program that will detect if there is a signal across various signal lines on a serial port. The signal would not be characters or anything, it would simply be a short, either on or off, but I have no idea where to start. I've been looking around on google and found some information on stuff like /proc/driver/tty/serial but I don't think I can use that. 

So yeah, looking for help to write a serial port monitor.

---

### Post by supirman on 2007-02-15
Minicom may be useful.  Also, interceptty may be useful.

I don't quite understand what you're wishing to monitor (signals across signal lines?) -- does that imply modem control signals?  If you're just wishing to read data, write a program that opens the appropriate tty and reads from it (most likely in a select() ).  You should be able to do something simple like this in python in a matter of a few minutes.

---

### Post by hatchek on 2007-02-15
All I want to detect from the serial port is if there is a physical connection between pins, for example if I put a shunt across pins 1 and 8, I'd want the program to sense this.

---

### Post by supirman on 2007-02-15
I don't know if that's possible.   Most PCs have a 16550 compatible UART, so you can look at the datasheet for the 16550 to see if there is such ability.  The voltage levels on the two pins ties together would be the same, that's about all I think you'd be able to tell.  


[http://www.national.com/ds/PC/PC16550D.pdf](http://www.national.com/ds/PC/PC16550D.pdf)

---

