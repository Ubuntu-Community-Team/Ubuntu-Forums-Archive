---
title: "gcc output"
date: 2007-04-16
forum: Programming Talk
---

### Post by richardhp on 2007-04-16
i have been googling for a while now to no avail and i looked at the man pages for gcc without success. I want to know how to compile a C source file into an object file as a flat file binary with no headers etc so i can then link it into an assembly progam i have written.

---

### Post by Arndt on 2007-04-16
> **richardhp said:**
> i have been googling for a while now to no avail and i looked at the man pages for gcc without success. I want to know how to compile a C source file into an object file as a flat file binary with no headers etc so i can then link it into an assembly progam i have written.

If gcc cannot be told to output exactly the format you want, maybe you can write a program to extract what you need from the ELF .o file. There may be tools for manipulating ELF files, I don't know. 'objdump' can be used to inspect headers, for example.

---

### Post by richardhp on 2007-04-17
ok thanks

---

