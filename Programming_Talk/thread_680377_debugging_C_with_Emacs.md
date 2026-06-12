---
title: "debugging C with Emacs"
date: 2008-01-27
forum: Programming Talk
---

### Post by bkelly on 2008-01-27
My computer is X86 with 64 bit Gutsy installed.  I have written a small C program, compiled and run it.  Now I want to step through it in the debugger using Emacs. (no problems, just leaning how.)  I can get it to step through the code in a fashion, but because of low knowledge level on my part, it seems rather erratic. 

How do I get Emacs so show the value of variables?

I recently used Microsoft Visual C# and could show the "locals" window which displays all the variables currently in scope.  As I step through the program, each variable is updated appropriately.

How close can I get to this under Linux?

Wow, I would do almost anything to have someone stand over my shoulders for an hour or two and guide me. (just wishful thinking)

Thanks for your time.

---

### Post by Lux Perpetua on 2008-01-28
Are you using GDB with Emacs? Type "print" or "p" and the name of the variable (as long as it is in scope).

---

