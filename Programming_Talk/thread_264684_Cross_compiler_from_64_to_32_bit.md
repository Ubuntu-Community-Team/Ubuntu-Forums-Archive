---
title: "Cross compiler from 64 to 32 bit?"
date: 2006-09-25
forum: Programming Talk
---

### Post by jmillikin on 2006-09-25
I've got a 64-bit computer that I'd like to put to work as a development system. As part of this, it needs to be able to build 32-bit binaries. I've been looking through the repos for a cross compiler, but the only ones available seem to be for unusual arches. How do I set up such a cross compiler?

---

### Post by pay on 2006-09-25
You could make a 32bit chroot and then compile 32 apps in that.

---

### Post by Mime on 2006-09-25
Yeah that'd probably be easiest.  Only other way I can think of offhand is by using the -m32 flag to force 32bit output, but that could get messy.

If you want to set up a cross compiler for something other than x86, that's a little more involved...

---

