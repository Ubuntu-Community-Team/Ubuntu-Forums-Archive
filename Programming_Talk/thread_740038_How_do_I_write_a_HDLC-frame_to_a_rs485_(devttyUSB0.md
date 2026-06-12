---
title: "How do I write a HDLC-frame to a rs485 (/dev/ttyUSB0)?"
date: 2008-03-30
forum: Programming Talk
---

### Post by trac on 2008-03-30
Hi!
I have a C-programming problem. I would like to write an asynchronous   HDLC-frame to my USB-port. On that port I have a converter to rs485 (2 wire). The converter gives me /dev/ttyUSB0 witch I can write to.

But how do I write a HDLC-frame to it?
The frame should start with 0x7E (01111110) then have 1 octet control, 1 octet address, N octet data, 2 octets CRC and at last a stop byte 0x7E.

Can I just open the tty in my program and write to it?
ex.
fd = open("/dev/ttyUSB0", O_RDWR);
write(fd, 0x7E, 1); 

Or does this send some bad chars out on the 2 wire as well?

---

