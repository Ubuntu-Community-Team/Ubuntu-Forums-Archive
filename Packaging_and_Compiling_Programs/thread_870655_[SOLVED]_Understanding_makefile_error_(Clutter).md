---
title: "[SOLVED] Understanding makefile error (Clutter)"
date: 2008-07-26
forum: Packaging and Compiling Programs
---

### Post by kid-pro-quo on 2008-07-26
I have just installed the latest (0.8) Clutter libraries. When I try to compile the included test programs using make I get an error.

make: *** No rule to make target `../clutter/libclutter-glx-0.8.la', needed by `test-textures'.  Stop.

If someone could give some guidance as to what is going wrong that would be greatly appreciated.

Cheers

---

### Post by kid-pro-quo on 2008-07-30
I managed to sort this out myself. I was just having a dumbass moment. I had forgotten to make install the clutter files before trying to make the test programs.

---

