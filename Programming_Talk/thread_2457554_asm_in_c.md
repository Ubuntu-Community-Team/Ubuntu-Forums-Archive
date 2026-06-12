---
title: "asm in c"
date: 2021-02-04
forum: Programming Talk
---

### Post by getchar2 on 2021-02-04
dear all, do you prefer insert assembly functions in your c programs using file.s or file.o ? and why? further...pushad is not available in amd64 , . how you insert inline assembly ? thanks kind regards

---

### Post by getchar2 on 2021-02-05
basically in this damn PIE system you can't compile c executables that use assembly functions. also -fpie doesn't work. yet some ubuntu experts certainly know how.

---

### Post by getchar2 on 2021-02-07
I managed to create a program c which calls assembly functions, bypassing the PIE, but it seems that ubuntu deems it deprecable, also the program works but generates a segmentation fault

---

### Post by getchar2 on 2021-02-07
also solved this problem;)

---

