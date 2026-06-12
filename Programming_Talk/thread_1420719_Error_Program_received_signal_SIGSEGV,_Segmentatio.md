---
title: "Error: Program received signal SIGSEGV, Segmentation fault"
date: 2010-03-03
forum: Programming Talk
---

### Post by sheperson on 2010-03-03
Hi,
I have compiled ns-2 on Ubuntu 9.10. Now when I try to run a simulation, I get segmentation fault error.
I tried gdb with ns (without debug enabled), and got this:
```

Program received signal SIGSEGV, Segmentation fault.
_IO_fread (buf=0xbfffd582, size=10, count=1, fp=0x0) at iofread.c:43
43      iofread.c: No such file or directory.                       
        in iofread.c

```I tried to enable debugging options in ns-2, using 
./configure --enable-debug
but I get many errors, so I have to compile ns-2 without debug enabled.

Does anyone have any idea what is going on?

Thanks.

---

### Post by dwhitney67 on 2010-03-03
The  file pointer being passed to an fread() or similar function is null.

How to fix this?  Who knows?  I don't know what part of the code is causing it, but for such a simple error, I would suspect that...

1.  You are using/running the application incorrectly;
2.  The original coders of the application are somewhat incompetent (ie they didn't write defensive code to protect against null-pointers);
3.  You built the application incorrectly.

As for item 3, is this application not available in the ubuntu application repository?

---

### Post by sheperson on 2010-03-04
> **dwhitney67 said:**
> The  file pointer being passed to an fread() or similar function is null.

How to fix this?  Who knows?  I don't know what part of the code is causing it, but for such a simple error, I would suspect that...

1.  You are using/running the application incorrectly;
2.  The original coders of the application are somewhat incompetent (ie they didn't write defensive code to protect against null-pointers);
3.  You built the application incorrectly.

As for item 3, is this application not available in the ubuntu application repository?

Hi,
Thanks for the tip. You are right, there was a null pointer passed to fread().
I found the piece of code causing the error, using gdb and backtrace.

Thanks again for your help.

---

