---
title: "Determine variable usage and size"
date: 2009-04-14
forum: Programming Talk
---

### Post by Sidneyaks on 2009-04-14
First off, sorry if this isn't allowed, but I read that faqs about homework and am pretty sure that it is.

Ok, so I'm writing a program for a class, and I was wondering, is there any easy way to use the terminal to just list out the variables the program creates and their types/size? I'm curious because I'm working with pointers and structures and it would help to know if I'm doing it right. Thanks in advance.

---

### Post by Can+~ on 2009-04-14
> **Sidneyaks said:**
> First off, sorry if this isn't allowed, but I read that faqs about homework and am pretty sure that it is.

Ok, so I'm writing a program for a class, and I was wondering, is there any easy way to use the terminal to just list out the variables the program creates and their types/size? I'm curious because I'm working with pointers and structures and it would help to know if I'm doing it right. Thanks in advance.

There are various ways to achieve that, for instance:

1. Manually creating a function that can print that information (easiest, but time consuming if the homework is updated often, well.. it depends on how big the homework is).

2. Compiling with debug flag (-gdb) and the passing it to a debugger or debugger front-end, and run it to check that's working ok.

---

### Post by Sidneyaks on 2009-04-14
Cool, I've seen my teacher use the debugger, but she types so fast that sometimes it's hard to keep up.

---

### Post by slavik on 2009-04-14
for sizes, look for "sizeof" in the index and how to use it. :)

---

