---
title: "Generic Kernel Hash Table"
date: 2009-06-11
forum: Programming Talk
---

### Post by Kebabman on 2009-06-11
Hi all,

Is there a generic hash table for use in the kernel (or a module for that matter). I am looking for something similar to the hcreate(), hsearch(), and hdestroy() family of functions that are available in userspace.

Any pointers appreciated.

---

### Post by Kebabman on 2009-06-11
Although I couldn't find a hash table implementation within the kernel this thread can be ignored now as I found [uthash]("http://uthash.sourceforge.net/") which does what I need quite nicely.

---

### Post by xsurfer on 2011-07-28
Hi,
I am doing a practice for an exam. I need to implement an Hash Table for use it in kernel. I saw uthash but it uses any lib available in user mode (stdlib).

I tried to study how other hash table are implemented (in /linux/include/pid.c) but I don't understand it (alloc_large_system_hash, where can I find docs for it (and other functions)?)

If anyone can help me, I'll be very gratefull.
Thanks in advance
Fabio

---

