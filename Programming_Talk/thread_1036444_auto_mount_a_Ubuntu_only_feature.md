---
title: "auto mount a Ubuntu only feature?"
date: 2009-01-10
forum: Programming Talk
---

### Post by 999alfred on 2009-01-10
I have a question about how ubuntu detects and auto mounts removable media, like thumb drives, CDs, cameras via USB, etc. Is this a special "Ubuntu kernel" feature, and if so where is the kernel archive?

I need to build a new kernel for my system since the 8,04 upgrade kernels no longer built the via82cxxx module, which caused my disk access to no longer use DMA which slowed my system to a crawl. Try 45secs to a minute to bring up a pdf in acroread.

Does the Ubuntu kernel come from a special place, or are patches need to be applied? I have found a kernel building guide, but it is just a list of commands. No explanation on what is happening or why you are doing it that way and I want a better understanding.

tj

---

### Post by jimi_hendrix on 2009-01-10
HAL daemon if i recall

---

### Post by OutOfReach on 2009-01-10
Yeah I believe that HAL (Hardware Abstraction Layer) does the auto mounting.
So any distro can auto mount if they have HAL...

---

