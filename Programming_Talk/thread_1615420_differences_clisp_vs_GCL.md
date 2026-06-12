---
title: "differences clisp vs GCL"
date: 2010-11-07
forum: Programming Talk
---

### Post by damonkashu on 2010-11-07
will any lisp programs I write function differently depending on if I load them in GCL 2.6.7 or CLISP 2.49?

---

### Post by worseisworser on 2010-11-07
Yes.

---

### Post by nvteighen on 2010-11-07
Yes, and this isn't restricted to Common Lisp: even though a certain language is standarized, every implementation of it will have its own particular features that may affect the way a program works. This usually happens when you use a non-standard extension or when the implementation of choice doesn't fully comply to the standard. An example: web browsers and HTML :(

---

