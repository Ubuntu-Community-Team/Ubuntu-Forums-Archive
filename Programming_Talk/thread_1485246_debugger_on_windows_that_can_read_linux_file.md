---
title: "debugger on windows that can read linux file?"
date: 2010-05-16
forum: Programming Talk
---

### Post by spider99 on 2010-05-16
Is there any debugger that operates on a Windows system that can read linux files? if so, then would someone list a few of the options?

---

### Post by MadCow108 on 2010-05-16
never did it but the gdb site says it runs under windows:
[http://www.gnu.org/software/gdb/](http://www.gnu.org/software/gdb/)
> 
GDB can run on most popular UNIX and Microsoft Windows variants.


---

### Post by trent.josephsen on 2010-05-16
If you're using a bytecode compiled language like Java, Perl, or Python, then any Windows debugger will do the trick.  But I suspect that isn't your problem.

No debugger is likely to debug executables compiled for any arbitrary Linux system while running on Windows.  For one thing, that would require an interpreter (more likely a JIT compiler of sorts) to make the Linux binary (ELF, I think) into a Windows executable (PE format).  On the fly.  That would be substantial bloat to a tool that was otherwise "just" a debugger.

If there's no way around it, you might look up cross-compiling (compiling your Linux executables on your Windows machine; I don't know how reasonable this is) OR using cygwin so that your Linux debugger is available in a Windows environment (keep in mind, though, that you wouldn't be debugging Linux native code, but Cygwin native code, which is something quite different).  I have never tried either of these methods but they both seem like an awful lot of trouble.

So the real question is:  Why?  If you have a Linux box available on which to run your program, why would you try to debug it under Windows?  If you want to develop under Windows (shudder), why are you writing Linux programs?  I'm not saying that there are no good reasons, but if you have a good reason, then you would probably not need to ask on the Ubuntu forums for answers (no offense).  So if you would pose us the problem, rather than what you think is the solution, we can probably help you better.  [Ask smart questions](http://catb.org/~esr/faqs/smart-questions.html).

---

