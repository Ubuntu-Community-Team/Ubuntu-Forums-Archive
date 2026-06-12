---
title: "kernel (oneiric) &gt; 3.0 compilation on &quot;maximus iv extreme&quot;"
date: 2011-08-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by masuch on 2011-08-20
Hi,

   I am running ubuntu 11.04 with natty kernel version 3.0.0-8 with catalyst 11.7 (or 11.8) on motherboard "maximus iv extreme" more or less  without problems.
   When I tried to compile new kernel 3.0.1 from source code with ubuntu oneiric patches according to this manual:

[http://duopetalflower.blogspot.com/2011/08/custom-kernel-301-ubuntu-64-bit-kernel.html](http://duopetalflower.blogspot.com/2011/08/custom-kernel-301-ubuntu-64-bit-kernel.html)

   It went into freeze black screen - no busybox, no console, no "ALT + SYSRQ + B" , just freeze - only cold reset works. 
   Catalyst driver has been always properly compiled with kernel/s.
   I tried to install oneiric kernel different versions (versions > 3.0 ) downloaded from ubuntu kernel web site and it behaves exactly the same way.  I also have installed those kernels on another ubuntu instances with the same results.
   My guess is - it looks like oneiric kernels does not work for this motherboard ?  :-(

Does anybody has similar problem with oneiric kernel on this motherboard?
Does anybody has successfully running oneiric kernel on maximus iv extreme motherboard?
Does anybody compile oneiric kernel and run it on this motherboard successfully?

Thank you very much for any clue to find out how to investigate or navigate where problem should be?

Martin

---

### Post by masuch on 2011-09-12
Finally it got to start working properly after using kernel version 3.0.3 and higher.

---

