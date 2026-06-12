---
title: "gdb assembly language question"
date: 2009-10-23
forum: Programming Talk
---

### Post by ltwinner on 2009-10-23
I declared a .float called my_value with a of 12.34 in the .section .data of my program. I then used gdb to debug the program.

I then type -
x/f &value - gdb displays 12.34000002
x/4b &value - gdb displays 0xa4 0x70 0x45 0x41
x/f &value - gdb displays 6.770504585.....e-220

What is going on here? Why is x/f &value showing a different answer than the first time I used it?

---

