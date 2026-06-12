---
title: "Linux kernel ABI and syscalls"
date: 2008-07-26
forum: Programming Talk
---

### Post by davidlt on 2008-07-26
Hello everyone,
I would need some help with Linux kernel and how to work with it.

I haven't done any ASM programming on Linux before. But it looks like Linux kernel ABI is similar to Windows one. I have managed to write some code already, compile it, link it and even run and it worked fine. But I need more information about ABI and of course syscalls list with all information about them, where I should put information, the return will be put, what kind of flags I can use and etc. The only thing that I managed to get find right now is syscall numbers and maybe files there those functions are located (not sure).

Is it possible to get this kind of information?

Thanks for the help,
david

---

### Post by NathanB on 2008-07-26
LSCR documents the syscalls:
[http://sourceforge.net/projects/lscr](http://sourceforge.net/projects/lscr)

and so does AsmRef:
[http://linuxasmtools.net/asmref.html](http://linuxasmtools.net/asmref.html)

for more information:
[http://www.int80h.org/](http://www.int80h.org/)

also explore this site:
[http://asm.sourceforge.net/](http://asm.sourceforge.net/)

Nathan.

---

### Post by ceclauson on 2008-07-26
I actually had the same question, and am grateful for the links that the previous poster put up :-)

---

