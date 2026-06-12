---
title: "sse3 on opteron"
date: 2007-10-15
forum: Programming Talk
---

### Post by nitro_n2o on 2007-10-15
Hi all, 
can somebody give me some pointer to where i can  find a tutorial on using sse3 instruction with AMD cpu's? 
Or even a general SSE3 instructions would also be great

couldn't find anything in Google

---

### Post by nitro_n2o on 2007-10-15
Opps!!! I believe that there are no see3 instructions on opteron, there is only sse and sse2 
so an sse2 tutorial in GCC would be great
thx,

---

### Post by psychicist on 2007-10-17
Newer Opterons do have SSE3 support but it's not called that way. You should look for "pni", which stands for Prescott New Instructions, when typing "cat /proc/cpuinfo". I don't have an Opteron but do have an Athlon64 with SSE3 support.

---

### Post by jespdj on 2007-10-18
For info on how to use SSE instructions in GCC, have a look at the GCC manual, especially section [5.43 Using vector instructions through built-in functions](http://gcc.gnu.org/onlinedocs/gcc-4.2.2/gcc/Vector-Extensions.html#Vector-Extensions).

There are a number of '__builtin_' macros that compile to vector instructions for the processor you're compiling your code for (SSE for x86, AltiVec for PowerPC, ...).

Alternatively, you could use inline assembly (see the GCC manual for how to do this exactly) and code assembler SSE instructions yourself. You can find out about which SSE instructions exists by reading Intel's [processor programming manuals](http://www.intel.com/products/processor/manuals/).

---

