---
title: "xsensors"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by The Hippie on 2013-03-11
I installed xsensors and i got confused coz there's so many temperatures. Theres temp1 = 40celsius, there's core0 temp at 42C another core0 temp at 50C, core1 temp at 56'C and another core1 temp at 44'C.


There's also another temp1 at 6,200'C.


Among them, what's the most important thing to look at?

And also there's no fan speed.

---

### Post by The Hippie on 2013-03-11
Thanks for any help.

---

### Post by The Hippie on 2013-03-11
Thanks for any help.

---

### Post by QIII on 2013-03-11
It is sometimes difficult to determine what is what.

What is your OEM and model of motherboard?  How about the CPU?

On your cores, I suspect what you have there is the CPU temp overall and the temp of each core.

---

### Post by The Hippie on 2013-03-12
> **QIII said:**
> It is sometimes difficult to determine what is what.

What is your OEM and model of motherboard?  How about the CPU?

On your cores, I suspect what you have there is the CPU temp overall and the temp of each core.
btw, does the core temp of 50'C too hot?

---

### Post by QIII on 2013-03-12
Probably.

Of course whatever is running a 6200 degrees is going to burn down to the core of the Earth anyway!  ;)

I can run my hexa-core full bore and it hovers right around 50 with a  Noctua NH-D14 CPU cooler.  The quad core on my @Home machine runs at 80%  24x7 at 44 degrees.

There are a couple of good reasons to figure out what all of those temperatures mean, especially the cores.  If you have two cores running at such a differential, something may be wrong with your cooling solution.  And, the CPU is running too hot if that is at idle.

So a bit of information about you hardware is in order.

---

