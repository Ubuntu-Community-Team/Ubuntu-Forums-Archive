---
title: "Serial port read problem (garbage)"
date: 2008-02-11
forum: Programming Talk
---

### Post by drorl on 2008-02-11
Hi.
I have a gps unit connected to my serial port.
When connecting it with hyper-terminal like linux program, i see all its output messages correctry as characters (NMEA format which is a gps protocol) and also as Hex codes of Ascii table.
But when i read the the port data into a buffer in a C++ program, using the read command, i get all kind of funny characters, with unused Hex codes.
Does anyone hvae any idea?
thanks
dror

---

### Post by hod139 on 2008-02-11
You will have to post some code for anyone to be able to help.

---

### Post by stroyan on 2008-02-11
It is likely that your program has not set the correct baud rate and parity for matching your device.
See [http://www.faqs.org/docs/Linux-HOWTO/Serial-Programming-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Serial-Programming-HOWTO.html)
for a discussion of the function calls that set those values.

---

