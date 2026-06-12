---
title: "Addresable Memory in a 32-bit processor."
date: 2008-04-18
forum: Programming Talk
---

### Post by shakeeb on 2008-04-18
Hi,
This is not a programming questions, but i figure most programmers should know.

My Questions is
How  much  memory can a 32-bit processor access ...? 

_My Calculations_
2^32 bits ==2^12 Mega_bits_==2^2 giga_bits_, 
but in reality the processor can access 2^2 Gig_bytes_ of memory. 
What am I doing wrong? I know I am doing something fundamentally wrong, but not sure what ...:mad:

Thanks

---

### Post by LaRoza on 2008-04-18
> **shakeeb said:**
> Hi,
This is not a programming questions, but i figure most programmers should know.

My Questions is
How  much  memory can a 32-bit processor access ...? 

_My Calculations_
2^32 bits ==2^12 Mega_bits_==2^2 giga_bits_, 
but in reality the processor can access 2^2 Gig_bytes_ of memory. 
What am I doing wrong? I know I am doing something fundamentally wrong, but not sure what ...:mad:

Thanks

It doesn't work that way. [http://en.wikipedia.org/wiki/32-bit](http://en.wikipedia.org/wiki/32-bit)

32 bits is the range in which the address can be encoded. The integer range of 32 bits is: 0 - 4,294,967,295. Any number larger than the upper limit would overflow and the address of the memory at the location would not be reachable. (Very simple, as there are ways around this)

---

### Post by stroyan on 2008-04-18
> **shakeeb said:**
> 
_My Calculations_
2^32 bits ==2^12 Mega_bits_==2^2 giga_bits_, 
but in reality the processor can access 2^2 Gig_bytes_ of memory. 
What am I doing wrong? I know I am doing something fundamentally wrong, but not sure what ...:mad:

You start with '2^32 bits'.  But each address corresponds to one byte.
The minimum addressable data is a byte.

---

### Post by shakeeb on 2008-04-18
> **stroyan said:**
> You start with '2^32 bits'.  But each address corresponds to one byte.
The minimum addressable data is a byte.
So each address of the 2^32 address can access 1 bytes, which would mean memory addressable =2^32*2^3=2^35 bits=2^5 Gigabits=2^2 Gigabytes=4GB ...
exactly what I was missing ...thanks :

---

