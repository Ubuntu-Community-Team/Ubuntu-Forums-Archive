---
title: "Missing Scheme Libraries???"
date: 2008-09-01
forum: Programming Talk
---

### Post by Lacrimstein on 2008-09-01
Hi,  today I decided to learn the language Scheme and installed the interpreter scm. Operators and data types work fine, however string operations procedures like "word", "first", "butfirst" seem to be missing because the compiler displays an error calling them "unbound variables". Maybe the standard library is missing? But SLIB is installed... any ideas?

---

### Post by Paul Miller on 2008-09-02
Which Scheme interpreter are you using?  Also, could you post the exact code you are trying that doesn't work?

---

### Post by nvteighen on 2008-09-02
Check how your interpreter imports data... Usually it's (require '<whatever>), if the libraries are in the interpreter's libs path. Otherwise, using the regular (load ...) should work.

---

