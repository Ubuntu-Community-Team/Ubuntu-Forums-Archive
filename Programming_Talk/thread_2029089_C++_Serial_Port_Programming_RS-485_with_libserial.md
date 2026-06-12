---
title: "C++ Serial Port Programming: RS-485 with libserial"
date: 2012-07-19
forum: Programming Talk
---

### Post by nmaster on 2012-07-19
I'm looking to communicate with a data acquisition board that uses RS-485.  I see that there is a C API for such communications:
[http://www.kernel.org/doc/Documentation/serial/serial-rs485.txt](http://www.kernel.org/doc/Documentation/serial/serial-rs485.txt)

However, I've also seen the libserial package ([http://libserial.sourceforge.net/](http://libserial.sourceforge.net/), in the repos)
which describes itself as "Simplified serial port programming in C++ under POSIX operating systems."  

In this situation (for this package) does "serial port" encompass _all_ types of serial ports or just RS-232 (the most common one)?

---

### Post by nmaster on 2012-07-20
perhaps to rephrase: which specific standards can be handled with libserial?

---

### Post by sajimon on 2012-07-21
Well, by the look of documentation it supports only rs232. That shouldn't be bad for You, as most rs485 fancy features comes on hardware layer, and communication is programmed as if it was rs232.

---

### Post by nmaster on 2012-07-21
> **sajimon said:**
> Well, by the look of documentation it supports only rs232. That shouldn't be bad for You, as most rs485 fancy features comes on hardware layer, and communication is programmed as if it was rs232.
could you elaborate a bit? this is my first experience with serial port programming :-/

---

### Post by trent.josephsen on 2012-07-21
From [http://en.wikipedia.org/wiki/RS-485](http://en.wikipedia.org/wiki/RS-485):

> EIA-485 only specifies electrical characteristics of the driver and the receiver. It does not specify or recommend any communications protocol.

<oversimplification>The communications protocol is software-side. The differences between RS-232 and RS-485 (full-duplex vs. half-duplex, and unbalanced vs. differential signaling) are generally resolved at the hardware level. From the CPU's standpoint, they behave the same.</oversimplification>

If you have RS-485 hardware, there's no reason I can see that you couldn't use libserial with it.

---

