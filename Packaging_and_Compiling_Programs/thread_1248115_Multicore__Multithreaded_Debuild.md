---
title: "Multicore / Multithreaded Debuild?"
date: 2009-08-23
forum: Packaging and Compiling Programs
---

### Post by korin43 on 2009-08-23
Is there anyway to make debuild run multiple threads? Like how you can do make -j5 to run make with 5 threads.

---

### Post by xtknight on 2009-08-25
Generally debuild -j8 or whatever you want will do it, but sometimes it's disabled for a particularly package in my experience.

---

