---
title: "Erratic GDB behavior"
date: 2009-05-07
forum: Programming Talk
---

### Post by ittiam on 2009-05-07
GDB is jumping up and down lines of code erratically and randomly. GDB sometimes show some lines of the code of being when actually they are not getting hit. But this behavior appeared after adding some macros. Could anyone throw some more light on this?

---

### Post by gmatt on 2009-05-07
I experienced the exact some behaviour in 8.10. I couldn't figure out what was going on so I had to switch back to 8.04 where I knew it was working fine. Note, I experienced this under KDevelop.

---

### Post by dwhitney67 on 2009-05-07
Did you recompile your source code after making changes to it?  Did you disable optimization when building your code?

---

### Post by ittiam on 2009-05-07
Yes I did a clean and make. I am not using any special optimization flags, just whatever is by default.

---

### Post by ittiam on 2009-05-07
dwhitney67, 

Apologies for the last incorrect post, actually optimization was enabled in another makefile (including multiple makefiles) and when i disabled it gdb started working smoothly. Thank you.

---

