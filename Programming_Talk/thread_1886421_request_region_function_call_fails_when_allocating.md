---
title: "request_region function call fails when allocating serial port registers"
date: 2011-11-24
forum: Programming Talk
---

### Post by sreeyeshns on 2011-11-24
I'm a professional C programmer. I'm learning device drivers and want to write (and test) a simple serial port driver to send characters at a baud rate of 9600. I've started writing the code.

The problem is the function request_region fails (returns NULL) when I try to allocate the serial port registers with address range 03f8-03ff. When I issue the command "cat /proc/ioports" I can see the following line

03f8-03ff : serial.

I thing this is because these ports are already allocated to already existing serial driver

Do I need to unload the already existing serial driver to test my driver? If so, how can I do that?

---

