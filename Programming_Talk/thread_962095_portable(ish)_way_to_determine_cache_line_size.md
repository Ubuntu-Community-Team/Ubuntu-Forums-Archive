---
title: "portable(ish) way to determine cache line size?"
date: 2008-10-28
forum: Programming Talk
---

### Post by Sydius on 2008-10-28
I found __builtin_prefetch to be exactly what I want, but I'm left wondering if there is something like it to determine the cache line size? I want to size the nodes in my linked list cache class to be that size if I can.

---

