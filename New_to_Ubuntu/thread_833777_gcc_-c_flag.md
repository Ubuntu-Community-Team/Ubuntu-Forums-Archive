---
title: "gcc -c flag"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Oddrey on 2008-06-18
I saw geany IDE used gcc -Wall -c "%f" to compile my C program, but I was wondering what -c does? Is it just another way to say -o?

---

### Post by Dr Small on 2008-06-18
From the GCC Manual:
```
       -c  Compile or assemble the source files, but do not link.  The linking
           stage simply is not done.  The ultimate output is in the form of an
           object file for each source file.

           By default, the object file name for a source file is made by
           replacing the suffix .c, .i, .s, etc., with .o.

           Unrecognized input files, not requiring compilation or assembly,
           are ignored.

```

---

