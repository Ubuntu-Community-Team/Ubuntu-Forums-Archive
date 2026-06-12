---
title: "[SOLVED] Seeking large files (C/C++)"
date: 2008-08-04
forum: Programming Talk
---

### Post by era86 on 2008-08-04
Greetings!

I am attempting to fseek() a large file (20-30gigs) and for some reason fseek() is returning -1.  Is this because fseek() cannot handle the large offset I pass to it?

If so, is there a way I can seek large files in C/C++?

Any help is appreciated, thank you!

---

### Post by era86 on 2008-08-04
Ok I figured it out...

Because the offset is so large, I have to use fseeko64() rather than fseek().

Marked as solved for others who run into the same stuff...

---

