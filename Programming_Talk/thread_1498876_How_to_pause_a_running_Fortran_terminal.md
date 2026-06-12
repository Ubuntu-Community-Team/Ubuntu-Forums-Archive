---
title: "How to pause a running Fortran terminal"
date: 2010-06-01
forum: Programming Talk
---

### Post by ashkan.rafiee on 2010-06-01
Hi guys,

I am very new to Linux. I was wondering if it is possible to pause a running FORTRAN program. I used to do this in Windows by right clicking on the running code > Edit > Mark.

Is there any equivalent for this in the Linux?

---

### Post by BoneKracker on 2010-06-01
It sounds like what you are talking about here is setting a breakpoint during debugging.  To do that, you need a debugger.  You were probably using a debugger that was integrated into an IDE.

You can install any of a large variety of IDEs in linux, or you can use an editor and the command-line tools that are part of GNU.  The GNU debugger is called "gdb".
[http://infohost.nmt.edu/tcc/help/lang/fortran/gdb.html](http://infohost.nmt.edu/tcc/help/lang/fortran/gdb.html)

The GNU Compiler Collection ("gcc") will also handle Fortran.  You can use these in a terminal, or through an IDE if you prefer (e.g., there is a Plugin for the Eclipse IDE called Phortran).

You can google for more information about Fortran on Linux

Edit: if you are talking about pausing an executing Fortran program, I would expect ctrl+z would do it, which pauses a task and places in the background. You can google about linux job control to get more information about that.

---

### Post by ashkan.rafiee on 2010-06-12
Thank you very much "BoneKracker" for very helpful comments.

---

