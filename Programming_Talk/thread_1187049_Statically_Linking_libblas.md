---
title: "Statically Linking libblas"
date: 2009-06-14
forum: Programming Talk
---

### Post by Otustelija on 2009-06-14
I'm trying to link a C program with libblas. I've installed libblas-dev. This works:
```
gcc -lblas test1.c
```

However, I want to link statically. This fails
```
gcc -static -lblas test1.c
```
with an undefined reference to e.g. cblas_ddot. Linking the .a file directly works:
```
gcc test1.c /usr/lib/libblas.a
```

However, I don't want to rely on having it in the same location elsewhere. What am I doing wrong?

---

### Post by stroyan on 2009-06-14
The problem is just a matter of link order.
When you link with -static, you need to carefully order archive libraries.
Code that uses a symbol must appear before the library that provides it.
You need to move "-lblas" so it appears after "test1.c".
```

gcc -static test1.c -lblas

```

That is different from what you are accustomed to with shared libraries
The linker just pulls in each shared library as a whole, so backward references work.

There are actually linker directives that will designate an unordered group of files.
But it can be much slower for large groups of files compared to sorting the library files.
```

gcc -static -Wl,--start-group -lblas test1.c -Wl,--end-group

```

---

### Post by Otustelija on 2009-06-14
Thanks, just what I was looking for!

---

