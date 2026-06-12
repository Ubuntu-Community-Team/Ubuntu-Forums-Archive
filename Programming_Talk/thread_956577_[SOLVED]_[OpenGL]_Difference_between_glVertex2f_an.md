---
title: "[SOLVED] [OpenGL] Difference between glVertex2f and glVertex2d?"
date: 2008-10-23
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-23
What is the difference between glVertex2d and glVertex2f? They both do the same thing!

---

### Post by snova on 2008-10-23
glVertex2f() takes floats as arguments and glVertex2d() takes doubles. There are also variants that take ints, and possibly others. That's it.

In general you should stick with the float versions, since that's what's used internally most of the time anyway. It saves a few type conversions.

---

