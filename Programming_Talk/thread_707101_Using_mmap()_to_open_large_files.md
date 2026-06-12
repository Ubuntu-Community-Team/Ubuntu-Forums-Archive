---
title: "Using mmap() to open large files"
date: 2008-02-25
forum: Programming Talk
---

### Post by kaklehona on 2008-02-25
Hi,
Does anyone know how I could use mmap() to open/read large files (about 4-5 Gbyte). I am programming in C/C++.

Edit: I found out that I can make my compiler pretend that it is a 64 bit machine by adding _FILE_OFFSET_BITS == 64, so now I can run my code without problems!

---

