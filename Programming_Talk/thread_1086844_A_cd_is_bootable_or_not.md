---
title: "A cd is bootable or not?"
date: 2009-03-04
forum: Programming Talk
---

### Post by oguzhantepe on 2009-03-04
Hi everyone.

Can anyone help me about how to determine a cd is bootable or not ?
the problem is it should be done with using java.

I m waiting for your help.

Thanx.

---

### Post by nvteighen on 2009-03-04
No idea, but that sounds as a job for a low-level language like C... or, at least, for a Java binding to a C library.

Are you sure Java supports that kind of operations?

---

### Post by oguzhantepe on 2009-03-04
thanx for your replay.
Have you got something to say me about how can I get this. is it possible to determine it with reading some specific sectors on cd with using shell commands? Firstly I should learn the key points. :)

---

### Post by jimi_hendrix on 2009-03-04
> **nvteighen said:**
> No idea, but that sounds as a job for a low-level language like C... or, at least, for a Java binding to a C library.

Are you sure Java supports that kind of operations?

yes, just use the java equivilent of system(""); that would return whats printed to the shell, parse output, and boom done

---

### Post by Can+~ on 2009-03-04
Wait, do you want to make a Bootable CD, or do you want to check if a CD is bootable or not?

---

### Post by oguzhantepe on 2009-03-05
Actually I want to check it with a piece of code or command in java environment.

---

### Post by nvteighen on 2009-03-05
> **jimi_hendrix said:**
> yes, just use the java equivilent of system(""); that would return whats printed to the shell, parse output, and boom done
No, that is not what I mean. That would just delegate the work to another program, not give your program the ability.

---

