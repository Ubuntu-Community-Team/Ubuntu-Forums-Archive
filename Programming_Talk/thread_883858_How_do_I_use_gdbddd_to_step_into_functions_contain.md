---
title: "How do I use gdb/ddd to step into functions contained in separate files?"
date: 2008-08-08
forum: Programming Talk
---

### Post by laptoplinux on 2008-08-08
I'm trying to use gdb or ddd to debug code, and the problem is occurring in a subroutine in a separate source file than the main program file.  How can I make gdb or ddd step into the subroutine source file and show me each line of the subroutine as it executes, and then jump back into the main file?

When I use gdb, telling it to step into the subroutine just makes it execute the whole subroutine at once, causing the crash.

When I use ddd, I can get it to step into the function, but it won't show which line it is currently on.  Trying to load the source file of the subroutine loads the file, but there is now marker to indicate which line the debugger is currently on.

---

### Post by nvteighen on 2008-08-08
What I do in gdb is setting a breakpoint in a proper line, e.g for file.c line 12:
```

break file.c:12

```

The program is paused and I do whatever I need. Then, just continue executing using "continue" (until next breakpoint) or "nexti" (step-wise) or "next" (step-wise skipping function calls).

To delete breakpoints, use "delete".

---

