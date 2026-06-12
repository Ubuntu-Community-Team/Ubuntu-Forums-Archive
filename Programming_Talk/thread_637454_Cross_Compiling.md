---
title: "Cross Compiling?"
date: 2007-12-11
forum: Programming Talk
---

### Post by dr_pressure on 2007-12-11
Hey guys... I've got a D-Link DSL-502Tadsl modem -- it runs linux but as far as I can tell has no package management whatsoever.

I'd really like to get a few basic tools on there (netcat, tcpdump, etc).

The box does have tftp on it, so I can easily get the files across.... the question is what do I have to do to get them to run.


cat /proc/cpuinfo tells me this:

> processor               : 0
cpu model               : MIPS 4KEc V4.8
BogoMIPS                : 149.91
wait instruction        : no
microsecond timers      : yes
extra interrupt vector  : yes
hardware watchpoint     : yes
VCED exceptions         : not available
VCEI exceptions         : not available


I know that MIPS is an IBM processor and I'm guessing that it probably doesn't run x86... so I suppose I need to cross compile an ELF binary for it.

Is it just as simple as putting an extra flag into gcc? (if not, I'd appreciate it if someone could point me in the direction of a user-friendly tutorial).

Am I going about this the right way?

---

### Post by the_unforgiven on 2007-12-11
> **dr_pressure said:**
> I know that MIPS is an IBM processor and I'm guessing that it probably doesn't run x86... so I suppose I need to cross compile an ELF binary for it.
No, [MIPS]("http://en.wikipedia.org/wiki/MIPS_architecture") is not an IBM processor - it was developed by MIPS Technologies.
> **dr_pressure said:**
> Is it just as simple as putting an extra flag into gcc? (if not, I'd appreciate it if someone could point me in the direction of a user-friendly tutorial).

Am I going about this the right way?
No, cross-compiling is not that easy - you would need a complete toolchain for cross-compilation (a toolchain includes a compiler - like gcc - and other required tools like the linker, an assembler and other required stuff). 
However, you might find the following links helpful:
[http://gcc.gnu.org/wiki/Building%20Cross%20Toolchains%20with%20gcc](http://gcc.gnu.org/wiki/Building%20Cross%20Toolchains%20with%20gcc)
[http://kegel.com/crosstool/](http://kegel.com/crosstool/)

The easier option would be to see if your distro's repositories already have a pre-built cross compiler toolchain.
For example, the embedded debian project has pre-built toolchains that you can use on Ubuntu as well:
[http://www.emdebian.org/tools/crosstools.html](http://www.emdebian.org/tools/crosstools.html)

HTH ;)

---

### Post by dr_pressure on 2007-12-11
Thanks mate, those pre-built tools look very promising :)

---

