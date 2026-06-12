---
title: "moving from java to bare metal access"
date: 2008-12-13
forum: Programming Talk
---

### Post by badperson on 2008-12-13
Hi,

I've worked only in java and perl as a programmer so far...I've never worked on any issues dealing with the ins and outs of a particular operating system, or dealing with hardware at all. 

I'm assuming C++ is the main language people write those types of apps, and I'm wondering what are the more difficult parts for someone coming from a java or perl background. 

thanks, 
bp

---

### Post by StOoZ on 2008-12-13
its usually C , but C++ will also do the trick , depends on what exactly you want to do.

---

### Post by badperson on 2008-12-13
so, for example, if you were going to write a driver for some hardware, say a soundcard, what issues would a java programmer not have confronted before?
thanks,
bp

---

### Post by CptPicard on 2008-12-13
The only thing that really comes to mind is how memory access is so much more explicit in many ways in C. Pointers and how to use them are the major difference.

---

### Post by pp. on 2008-12-13
Timing, interrupts, exclusive control of the processor are other topics which come to mind, as well as ambiguous data types.

---

### Post by Cracauer on 2008-12-13
> **badperson said:**
> Hi,

I've worked only in java and perl as a programmer so far...I've never worked on any issues dealing with the ins and outs of a particular operating system, or dealing with hardware at all. 

I'm assuming C++ is the main language people write those types of apps, and I'm wondering what are the more difficult parts for someone coming from a java or perl background. 

thanks, 
bp

If you stay in userland you just use whatever language they give you an API for the functionality you want. Obviously, there is a C API for everything that's directly coming from kernel code, it's called system calls, the more obscure stuff often doesn't have their own system calls but uses ioctl as a hack. You can argue that /proc and /sys stuff isn't a C API at all, it's ... I dunno, a /bin/cat interface?

If you want to move from userland to actual kernel code it's just C, unless you want to go through the trouble of a userland driver.

So what are you trying to do?

If you just need to fiddle with a certain piece of hardware you need to look at the API(s) exported by whoever did the driver.

---

