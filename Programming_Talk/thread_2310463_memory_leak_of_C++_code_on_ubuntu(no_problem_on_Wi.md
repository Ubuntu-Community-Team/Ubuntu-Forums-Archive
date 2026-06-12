---
title: "memory leak of C++ code on ubuntu(no problem on Windows)"
date: 2016-01-19
forum: Programming Talk
---

### Post by newcfd on 2016-01-19
Why does the same C++ code have memory leak on Ubuntu, but no problem on Windows?
Or maybe not be memory leak. Linux simply does not release the memory. I tried the same code on CentOS and have the same problem.

---

### Post by spjackson on 2016-01-20
How are detecting and measuring the memory leak? Are you using valgrind? If there is a genuine leak, we would really need the code in order to help.

---

