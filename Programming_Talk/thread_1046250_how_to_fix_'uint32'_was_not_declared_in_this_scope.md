---
title: "how to fix: 'uint32' was not declared in this scope ?"
date: 2009-01-21
forum: Programming Talk
---

### Post by mangar on 2009-01-21
I'm porting some code from Windows to Linux.
I need to use a DWORD (hardcoded 32 bit variable),
when I try to use uint32, I get the following error:

'uint32' was not declared in this scope

I compiled the code using g++.
what am I missing?

---

### Post by Zugzwang on 2009-01-21
These types are not standardised. Under Linux, one normally uses "uint32_t".

See here: [http://linux.die.net/man/3/uint32_t](http://linux.die.net/man/3/uint32_t)

Many libraries (e.g. SDL) define their own types in order to fix the problems of different type names on certain platforms. You can include one of these and use the type names provided for cross-platform compatibility.

---

### Post by mangar on 2009-01-21
Thanks, it worked!

---

