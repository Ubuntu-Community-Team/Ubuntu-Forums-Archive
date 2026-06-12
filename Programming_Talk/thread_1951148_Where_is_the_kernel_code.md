---
title: "Where is the kernel code?"
date: 2012-04-02
forum: Programming Talk
---

### Post by DBQ on 2012-04-02
Hi everybody.

In the physical memory of the system, does the kernel code always reside at the same physical address range?

Thank You!

---

### Post by CynicRus on 2012-04-02
The kernel at boot time usually takes the form image file, a compressed format zImage or bzImage using zlib. It provides an umbrella program that spends a minimum hardware configuration, decompresses the image entirely in upper memory and mounts RAM-disk, if applicable. After that, it executes the kernel and the process by ./arch/i386/boot/head startup_32 () (for a family of processors x86).

Based on that - assuming that it is loaded by the dynamic address.

---

### Post by idoitprone on 2012-04-02
> **DBQ said:**
> Hi everybody.

In the physical memory of the system, does the kernel code always reside at the same physical address range?

Thank You!

No I dont think it is in the same physical address range, but i am not sure. I guess this should be answer by a kernel developer or hacker which i am neither
Since the kernel impliments this security technique, it should be different every time
but i do not know if the kernel randomize its address space at boot

[http://en.wikipedia.org/wiki/Address_space_layout_randomization](http://en.wikipedia.org/wiki/Address_space_layout_randomization)

---

