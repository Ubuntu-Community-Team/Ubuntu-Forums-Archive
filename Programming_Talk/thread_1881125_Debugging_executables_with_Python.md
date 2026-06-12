---
title: "Debugging executables with Python"
date: 2011-11-15
forum: Programming Talk
---

### Post by Drezard on 2011-11-15
Hey guys,

Building a fuzzer in Python.

I want to debug c coded executables in python. Is there an API for gdb or a better way of doing it?

Cheers,

Drez

---

### Post by ofnuts on 2011-11-15
> **Drezard said:**
> Hey guys,

Building a fuzzer in Python.

I want to debug c coded executables in python. Is there an API for gdb or a better way of doing it?

Cheers,

DrezYou question doesn't really make sense... I don't think you want to write a debugger in Python. If you want debug a C extension to python, they you have to debug the Python executable and set the breakpoints in your code.

---

