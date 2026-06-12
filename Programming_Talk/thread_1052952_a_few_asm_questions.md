---
title: "a few asm questions"
date: 2009-01-28
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-28
ok so i am learning asm to learn more about the machine, but i have a few questions:

1) can someone show me how to get input via syscalls? (nasm preferably)
2) i prefer nasm, but what would i find more literature for, nasm or gas (tutorial wise)
3) i have a 64-bit machine, but all the tutorials use 32-bit, ld complains when i try to link non-elf64 format object files, anyway i can compile 32-bit code?
4) i dont quite understand the call convention thing with the stack, can anyone clearify it?

edit: scratch number one, some experimenting and manpage look ups and i got it

---

### Post by NathanB on 2009-01-28
> **jimi_hendrix said:**
> ok so i am learning asm to learn more about the machine, but i have a few questions:

1) can someone show me how to get input via syscalls? (nasm preferably)

You make me proud.

> 2) i prefer nasm, but what would i find more literature for, nasm or gas (tutorial wise)

I think they are both about equal on that score.  But more programmers use nasm, so it generally is a better choice for learning.

> 3) i have a 64-bit machine, but all the tutorials use 32-bit, ld complains when i try to link non-elf64 format object files, anyway i can compile 32-bit code?

64-bit literature **does** exist -- just not in abundance.  :)

Here is what I've located so far:

[http://www.viva64.com/links/64-bit-development/](http://www.viva64.com/links/64-bit-development/)

[http://www.vikaskumar.org/wiki/index.php?title=X86-64_Tutorial](http://www.vikaskumar.org/wiki/index.php?title=X86-64_Tutorial)

[http://msdn.microsoft.com/en-us/library/ms794533.aspx](http://msdn.microsoft.com/en-us/library/ms794533.aspx)

[http://www.x86-64.org/](http://www.x86-64.org/)

[http://www.amd.com/us-en/Processors/DevelopWithAMD/0,,30_2252_869_875](http://www.amd.com/us-en/Processors/DevelopWithAMD/0,,30_2252_869_875)...

[http://www.intel.com/products/processor/manuals/index.htm](http://www.intel.com/products/processor/manuals/index.htm)

> 4) i dont quite understand the call convention thing with the stack, can anyone clearify it?

Rather than trying to explain it in a short post here, I hope you don't mind a few links to quality resources.

[http://en.wikipedia.org/wiki/X86_calling_conventions](http://en.wikipedia.org/wiki/X86_calling_conventions)

You'll need to register on the forum to download this pdf, but the tutorial does an excellent job of explaining the C calling convention and different schools-of-thought about dealing with the stack:

[http://www.daniweb.com/forums/thread41309.html](http://www.daniweb.com/forums/thread41309.html)

Hope that helps!

---

### Post by jimi_hendrix on 2009-01-28
ok...one more thing (at now at least...)

if i push 3 on the stack, then call a function, how do i pop 3 in my function without messing up the place that the function will return to

edit: ok got it....push qword 3

but how would i call a C function (printf("%d",42);)

---

### Post by NathanB on 2009-01-28
> **jimi_hendrix said:**
> ok...one more thing (at now at least...)

if i push 3 on the stack, then call a function, how do i pop 3 in my function without messing up the place that the function will return to

edit: ok got it....push qword 3

No, you wouldn't want to POP the arguments inside the function.  Simply access it with a 'mov rax, [esp + 8]' for instance.

> but how would i call a C function (printf("%d",42);)

This is demonstrated in that PDF I talked about.  Simply push the arguements onto the stack in reverse order:  first push the 42, then push the address of the "%d" format string, then call printf, then clean-up the stack by adjusting ESP accordingly.

One thing that might be helpful is to examine the code that the C compiler generates.  You can use the "-S" option to GCC for this.

If you don't like (G)AS syntax, then use 'objconv' to produce a more readable disassembly:

[http://www.agner.org/optimize/#objconv](http://www.agner.org/optimize/#objconv)

---

