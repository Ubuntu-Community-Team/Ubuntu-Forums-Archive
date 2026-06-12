---
title: "Quick question about &quot;a.out&quot; in C"
date: 2009-12-30
forum: Programming Talk
---

### Post by grantbourquehelp on 2009-12-30
I'm a programming newbie and I was just wondering if there is any reason to compile C files into "a.out" instead of just using the -o command in gcc. Is there any use to a.out files that I can't do with the files produced by gcc -o? Thanks.

---

### Post by Queue29 on 2009-12-30
There is nothing special about it, it's just a default name.

---

### Post by MaxIBoy on 2009-12-30
It was for historical reasons. It used to be that the format for executable files was called "a.out," so the name was descriptive (like adding ".txt" for text, on UNIX it serves no purpose other than description.) Later on, we switched to other formats (Linux uses ELF,) but the default name was kept.

---

