---
title: "Some question about Assembly Language"
date: 2012-04-05
forum: Programming Talk
---

### Post by prismctg on 2012-04-05
What is the advantage of learning assembly language?
how do it works in practical life?

---

### Post by santosh83 on 2012-04-05
> **prismctg said:**
> What is the advantage of learning assembly language?
how do it works in practical life?

You get an insight into how your processor works that's not possible at a higher level. You also get an idea of the form of instructions all higher-level languages must finally be translated into, i.e., you learn approximately the processor's language, rather than making it learn your language (HLLs.)

This enables you to avoid certain grossly inefficient high-level programming constructs, and speed up hot-spots by rewriting them in assembly (if needed.) In system and graphics programming there are many places where you **must** use assembly, so learning an assembly language helps there as well.

There are many assembly dialects, just like there are many HLLs.

---

### Post by Redblade20XX on 2012-04-05
Just from the top of the head. Well when you look into assembly, you get a better view of how the system "physically" works.  It's useful for many things such as if you want to create an embedded system or design a compiler.

---

### Post by CynicRus on 2012-04-05
In my opinion, assembly needed in the first place - working with the hardware directly, as well as - for equipment with low memory, where at times to save bytes of memory cycles needed to expand the line. Knowledge of assembly language - definitely helps in the development of system software, and of course debugging. And also - in the study of software where the source code is unavailable.

---

### Post by lisati on 2012-04-05
One of the advantages of using assembly language is that you can sometimes do things better and more efficiently using it. There are times when it's the only practical way to get something done.

A big disadvantage is that it usually limits you to a particular family of processors, or even one particular processor. This is no good if you are interested in portability.

---

### Post by alexfish on 2012-04-05
> **lisati said:**
> One of the advantages of using assembly language is that you can sometimes do things better and more efficiently using it. There are times when it's the only practical way to get something done.

A big disadvantage is that it usually limits you to a particular family of processors, or even one particular processor. This is no good if you are interested in portability.

There are cross assemblers for portability

[http://wiki.answers.com/Q/What_is_the_cross_assembler](http://wiki.answers.com/Q/What_is_the_cross_assembler)

could also look to using with Qemu for testing

Have fun

alexfish

---

### Post by prismctg on 2012-04-05
Thanx a lot :)

---

