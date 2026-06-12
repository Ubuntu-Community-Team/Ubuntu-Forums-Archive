---
title: "Where are my headers?"
date: 2008-11-27
forum: Packaging and Compiling Programs
---

### Post by skippylou on 2008-11-27
Hi, I have a new installation of ubuntu 8.04.  I run make for a simple application. gcc gives lots of errors: cannot find stdio.h, stdlib.h, string.h &ct.  As these are standard C files I think it must me some kind of path problem. Cannot find any of these headers in the filesystem.  What is going on?  I am very new to ubuntu but have been using C compilers before linux was invented.  

Skippy

---

### Post by jpkotta on 2008-11-27
Did you install build-essential?

Most of the headers are in /usr/include/.

---

