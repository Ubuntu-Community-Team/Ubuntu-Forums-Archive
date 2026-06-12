---
title: "Anybody know of any C language tools?"
date: 2007-12-10
forum: Programming Talk
---

### Post by ameba on 2007-12-10
8

---

### Post by rufius on 2007-12-10
Gcc? Pcc?

---

### Post by ameba on 2007-12-10
t

---

### Post by samjh on 2007-12-10
PCC = Portable C Compiler ([link](http://en.wikipedia.org/wiki/Portable_C_Compiler))

Forget about PCC.  Use GCC, because GCC is the de facto standard compiler for the C programming language for Linux.  If you have requirements that cannot be satisfied using GCC, then search for other C compilers (TCC, SDCC, Mingw32, Digital Mars, etc).

---

### Post by LaRoza on 2007-12-10
tcc is also very good, it is for Windows and Linux and is an interpreter also.

For programming in C in Linux, ```

sudo aptitude install build-essential

```

---

