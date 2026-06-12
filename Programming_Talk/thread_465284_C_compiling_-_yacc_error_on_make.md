---
title: "C compiling - yacc error on make"
date: 2007-06-05
forum: Programming Talk
---

### Post by haftan on 2007-06-05
yacc -d gram.yx
make: yacc: Command not found
make: *** [gram.h] Error 127

I have been trying a 'make' on a new Dell/Ubuntu laptop (with programs from an older Dell/RedHat workstation).  I have been updating the libraries bit by bit using this forum to resolve each error in make... but the most recent error has me stumped.  What do I need to install next?

---

### Post by WW on 2007-06-05
To get yacc, install the package **bison**:
```

$ sudo apt-get install bison

```
(or use Synaptic to install it).

---

