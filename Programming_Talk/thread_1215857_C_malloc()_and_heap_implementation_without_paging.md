---
title: "C malloc() and heap implementation without paging"
date: 2009-07-17
forum: Programming Talk
---

### Post by Troy Martin on 2009-07-17
Hi there,

I'm currently looking for a malloc()/free() implementation for my hobby C kernel (not linux or BSD or anything else known to the world) that ***DOES NOT*** use paging. I have yet to implement paging in my kernel, and I don't think I will anytime soon, but I would like to implement dynamic memory allocation so I don't start plopping countless bytes into the kernel's .bss section (I've heard GRUB can be a pain in the @$$ if it has to zero out a really large .bss...)

My project is under the BSD license, so a BSD or PD implementation would be really great (please please PLEASE no GPL or LGPL code...)

Thanks,
Troy

---

### Post by smartbei on 2009-07-18
How about writing your own malloc/free functions that just for now just use a block of contigious memory, so that the kernel's code is ready for using dynamic memory. Later on (when you have paging set up) you can just change the function's implementation and have it truly allocate dynamically.

---

