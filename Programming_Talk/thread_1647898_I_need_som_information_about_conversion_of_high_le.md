---
title: "I need som information about conversion of high level language to assembly level"
date: 2010-12-18
forum: Programming Talk
---

### Post by Gopal Mondal on 2010-12-18
Hello everyboy.

I have dissasembled a C program by cc -S program name.

But i did not understand from which memory loaction the program loads and there is first few lines of main function.

0x080483e4 <+0>: push %ebp
0x080483e5 <+1>: mov %esp,%ebp
0x080483e7 <+3>: and $0xfffffff0,%esp
0x080483ea <+6>: sub $0x20,%esp


1. where ebp is pushing?(the adress)
2. why we need to mask off the last four bits?
3.why esp is moving to next 20 memory loaction?

---

### Post by trent.josephsen on 2010-12-18
> **Gopal Mondal said:**
> I have dissasembled a C program by cc -S program name.
Erm, no.  You *compiled* a C program, without assembling it.

If you're new to x86 assembly, the output of a compiler probably isn't the best place to start.  (If you're new to assembly, x86 probably isn't the best place to start, either.)  Start with an assembly tutorial -- others can suggest better than I -- and learn how to read human-written code before you tackle the commentless output of a compiler.

---

### Post by saulgoode on 2010-12-18
> **Gopal Mondal said:**
> 1. where ebp is pushing?(the adress)

The contents of EBP are pushed onto the return stack (pointed to be ESP). The EBP is used to point to [stack frames]("http://en.wikipedia.org/wiki/Call_stack#Structure") which is where local variables are stored. The EBP is being saved on the return stack so that it can be restored (to the calling program's stack frame location) when your program exits.

> **Gopal Mondal said:**
> 2. why we need to mask off the last four bits?

It is a requirement of some floating point (and/or SSE2) instructions that their arguments be aligned to 16-byte addresses (otherwise, 4-byte alignment would've been sufficient).

> **Gopal Mondal said:**
> 3.why esp is moving to next 20 memory loaction?

Because you are reserving the space (between ESP and EBP) for storage of local variables.

---

### Post by Gopal Mondal on 2010-12-19
thank you for the great information..:)

---

