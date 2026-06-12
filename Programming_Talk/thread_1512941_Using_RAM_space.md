---
title: "Using RAM space"
date: 2010-06-18
forum: Programming Talk
---

### Post by yousafsajjad on 2010-06-18
I need to use some memory from RAM .. I not sure where but I read somewhere that there is some small space in the RAM close to Interrupt vector table (IVT) that a user application could  use ... In fact it is for the BIOS to use ... so does anyone know what  is the address range for it .. or anything related to it ?

---

### Post by schauerlich on 2010-06-18
EDIT: i misunderstood your question.

---

### Post by pbrane on 2010-06-18
Have a look at this:
[http://wiki.osdev.org/Memory_Map_%28x86%29]("http://wiki.osdev.org/Memory_Map_%28x86%29")
I don't think you can use BIOS memory. You might be thinking of the first 640K below the BIOS upper 384K of the first 1M of RAM.

---

### Post by soltanis on 2010-06-18
On any machine with a functioning multiprocessor kernel and MMU, you can't arbitrarily pick parts of memory for your own use. Instead, depending on the language you are using, memory will be allocated for you automatically (on x86 machines, it is allocated on the "stack"), or if you need to allocate memory in a more dynamic fashion (based on changing runtime requirements) you ask the kernel for more memory.

Without more information on what language you are using or what platform you're developing on I really can't tell you how you should go about doing that.

You can read the following documentation for more information on these general ideas:

[http://en.wikipedia.org/wiki/Automatic_memory_allocation](http://en.wikipedia.org/wiki/Automatic_memory_allocation) - for so called "automatic" variables, whose memory is set aside by virtue of you declaring them
[http://en.wikipedia.org/wiki/Dynamic_memory_allocation](http://en.wikipedia.org/wiki/Dynamic_memory_allocation) - more on the concept
[http://linux.die.net/man/3/malloc](http://linux.die.net/man/3/malloc) - malloc is a C function call for allocating heap memory, from the standard library
[http://linux.die.net/man/2/sbrk](http://linux.die.net/man/2/sbrk) - the underlying system call which performs the heap memory allocation

---

