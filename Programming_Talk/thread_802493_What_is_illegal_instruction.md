---
title: "What is illegal instruction?"
date: 2008-05-21
forum: Programming Talk
---

### Post by pacofvf on 2008-05-21
I'm programming in gtk and i get a strange error sometimes: "illegal instruction " what does it really means? i think its like segmentation fault, the code that make this error has been checked by lots of friends and we can't see any error,  if somebody could explain to me what is illegal instruction i would appreciate it very much. thanks.

---

### Post by Can+~ on 2008-05-21
You could post the code, say what language you're using, etc.

I'll guess you're using C. Try running it on a debugger and see where it  fails, I would suggest gdb, but it's really hard to use it, so install Eclipse with the c plugin (cdt) (everything on the repositories), or the debugger kdbg.

---

### Post by jespdj on 2008-05-21
"Illegal instruction" means that the processor is trying to execute something in a program that is not a valid machine instruction opcode.

When this happens, it means that your program has gotten into a bad state - maybe there's data corruption which confuses your program. It can also happen if you compile your program the wrong way - for example, if you tell the compiler to generate SSE3 instructions and the computer you're running the program on has an older processor that doesn't have SSE3 instructions.

If you have a specific piece of code that produces the problem, then post that code here, and people might be able to tell you if there's something wrong with it.

---

