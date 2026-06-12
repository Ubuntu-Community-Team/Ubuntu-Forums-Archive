---
title: "Accessing ttyUSB0 directly with ioperm() and outb()?"
date: 2007-11-24
forum: Programming Talk
---

### Post by maierm on 2007-11-24
Hi all,

I've got a question on how to control the pins (e.g. TXD) of a (USB) converted RS-232 port from a C program.

I do know how to access the registers of "real" serial ports, by using ioperm() and outb(). Now I'd like to use the same approach with an USB-RS232 adapter.

Does anyone know if this is possible? And if yes, how can I find out the base address of ttyUSB0, for instance?

Thanks in advance,

Andre

---

