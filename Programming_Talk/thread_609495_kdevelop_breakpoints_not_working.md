---
title: "kdevelop breakpoints not working"
date: 2007-11-11
forum: Programming Talk
---

### Post by map7 on 2007-11-11
I've just installed Ubuntu 7.10 and kdevelop 3.5.0.

The debugging in kdevelop is not working, in the sense that I set a breakpoint and it doesn't stop there.

I have tried this with the hello world sample template program, entering a breakpoint on the print line, and it skips it for some reason.

What possible have I missed here?

---

### Post by baxeico on 2008-04-02
Did you compile with debugging information? Check if -g flag is in your compilation command.

---

