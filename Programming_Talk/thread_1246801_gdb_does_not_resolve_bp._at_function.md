---
title: "gdb does not resolve bp. at function"
date: 2009-08-22
forum: Programming Talk
---

### Post by Pla1n on 2009-08-22
Hi. Im tryin to learn some debugging and asm.
I have problem when I set a breakpoint at strcpy().
gdb ask me if I want to set bp. after loading the library
but It does not resolve the breakpoint and skip func so I cant examine it.
Enough rant. Think the log is quite clear: [http://pastie.org/591381](http://pastie.org/591381)

first par is my problem and second is how it should looks.
So, where is my mistake?

Thanks in advance :)

---

### Post by dwhitney67 on 2009-08-22
It appears that you want to set a breakpoint at the point in the program where strcpy() is called.  It looks like you have done that.  Once the breakpoint is hit, the next thing you want to do is "step" into the function, not "cont".

Now, for the bad news.  Typically the C library is stripped of all debugging symbols (so as to make the library more compact/smaller/optimized), thus you may not be able to "step" into the function at all.

Final note... your usage of printf() in your small program is incorrect.  You need a format statement; in your case, a "%s\n", before the parameter you have supplied.

If you know that you will print a string, alternatively you can use puts().

---

### Post by Pla1n on 2009-08-24
I have finally the solution. When compile it with just -g param then the program is optimized: strcpy to memcpy and printf to puts [http://codepad.org/SteUv4cs](http://codepad.org/SteUv4cs) . It is needed to add -fno-builtin parameter then I can examine inside strcpy function.

---

