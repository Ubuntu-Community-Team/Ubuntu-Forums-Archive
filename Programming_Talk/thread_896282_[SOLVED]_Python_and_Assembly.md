---
title: "[SOLVED] Python and Assembly"
date: 2008-08-21
forum: Programming Talk
---

### Post by jinksys on 2008-08-21
Does Python have *native* support for inline assembly?

---

### Post by pmasiar on 2008-08-21
Of course not. Python is multiplatform high-level language. It it compiles to and then executes bytecode (virtual machine).

It you need speed, write code in C and link it to your Python. Or use Cython.

Why you need it: is speed a problem? Or you are just a speed kiddie?

---

