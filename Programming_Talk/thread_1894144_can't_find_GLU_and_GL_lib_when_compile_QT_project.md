---
title: "can't find GLU and GL lib when compile QT project"
date: 2011-12-11
forum: Programming Talk
---

### Post by skdjfsk on 2011-12-11
Hello, everybody, I meet a problem when compile Qt project,The information is "can't find GLU and GL lib", I find there's "-lGLU -lGL" in makefile, Does anyone meet problem like this, what should I do?

---

### Post by Zugzwang on 2011-12-12
Please copy and paste the precise error message here. "can't find GLU and GL lib" does not seem to be copied and pasted (because of informality).

Then, try to compile your project from the terminal (if you didn't do so) and copy all of the the output here, because then we can see how precisely the GNU compiler/linker is called and what is the likely cause of the problem.

---

### Post by MadCow108 on 2011-12-13
most likely you do not have the correct dependencies installed (e.g. libgl1-mesa-dev and libglu1-mesa-dev packages) or there is a bug in the configure script
it probably test links to check if the libraries are there but orders the commandline incorrectly.

the -lGLU and -lGL must be at the end of the command line, in configure script that usually translates to placing these flags in the LIBS environment variable and not LDFLAGS or CFLAGS

---

