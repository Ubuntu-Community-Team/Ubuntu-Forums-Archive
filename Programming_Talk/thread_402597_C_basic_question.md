---
title: "C basic question"
date: 2007-04-05
forum: Programming Talk
---

### Post by Boule on 2007-04-05
Hi,

Probably a dumb question...
I was trying to write a small C program, saved the C file in my home directory, and when I compiled (gcc), I got: "error: stdio.h: no such file or directory"

Do I need to install something to make it work ? I'm used to this working out of the box on linux distros...

Thanks for your help

---

### Post by WW on 2007-04-05
You probably have not installed libc6-dev.  To get the basic set of C/C++ tools and libraries, install the package **build-essential**.
E.g.
```

$ sudo apt-get install build-essential
```

---

