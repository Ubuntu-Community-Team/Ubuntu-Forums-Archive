---
title: "python building specific udp packet"
date: 2009-06-12
forum: Programming Talk
---

### Post by anonmars on 2009-06-12
Hello,

I am familiar with the basic socket functions in Python (sending data over TCP, UDP, etc.), however, I have a C program that's expecting data in a certain format:

an integer value in 2 bytes and
an integer value in an 8 byte amount of space

How can I build and send such a specific packet with python? I.e. what libraries and/or functions/capabilities would even allow me to do this?

Thanks.

---

### Post by soltanis on 2009-06-12
[http://www.python.org/doc/2.5.2/lib/module-struct.html](http://www.python.org/doc/2.5.2/lib/module-struct.html)

I think that is what you want; specifically, the first integer you mentioned (assuming this is an i686 arch) would be on an Intel a "short"; the second one would be a "long".

Pay attention to byte ordering and width especially if these programs are running on two different systems. Intel x86's order little endian, and the gcc compiles integers to these widths on this platform:

unsigned/signed char - 8 bits
unsigned/signed short - 16 bits (2 bytes)
unsigned/signed int - 32 bits (4 bytes)
unsigned/signed long - 64 bits (8 bytes)

---

