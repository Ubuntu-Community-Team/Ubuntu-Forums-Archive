---
title: "makefile problem in C"
date: 2011-01-22
forum: Programming Talk
---

### Post by technmom on 2011-01-22
I'm running Ubuntu 10.04 I need to compile several programs and would like to put them in a makefile. I did do that but only the first one compiles. Obviously, this isn't a sophisticated makefile because it is my first. Please help

```

 Variable CC will is the compiler to use.
gcc=$(CC)

matmul500: matmul500.c
    $(CC) -o matmul500 matmul500.c
matmul800: matmul800.c
    $(CC) -o matmul800 matmul800.c

matmul_mod_5_500: matmul_mod_5_500.c
    $(CC) -o matmul_mod_5_500 matmul_mod_5_500.c

matmul_mod_5_800: matmul_mod_5_800.c
    $(CC) -o matmul_mod_5_800 matmul_mod_5_800.c

matmul_mod_10_500: matmul_mod_10_500.c
    $(CC) -o matmul_mod_10_500 matmul_mod_10_500.c

matmul_mod_10_800: matmul_mod_10_800.c
    $(CC) -o matmul_mod_10_800 matmul_mod_10_800.c



```

---

### Post by Vox754 on 2011-01-22
> **technmom said:**
> I'm running Ubuntu 10.04 I need to compile several programs and would like to put them in a makefile. I did do that but only the first one compiles. Obviously, this isn't a sophisticated makefile because it is my first. Please help
...


Well, if you want to create several executables you need a rule that specifies them as requisites, so it will create them all. Also, the first rule is the default one (just run "make"), so you want to make sure this one builds your entire project.

```

all : matmul500 matmul800 matmul_mod_5_500

matmul500: matmul500.c
    $(CC) -o matmul500 matmul500.c
matmul800: matmul800.c
    $(CC) -o matmul800 matmul800.c

matmul_mod_5_500: matmul_mod_5_500.c
    $(CC) -o matmul_mod_5_500 matmul_mod_5_500.c


```

---

### Post by technmom on 2011-01-22
Thanks .........worked like a charm! Love this forum!

---

