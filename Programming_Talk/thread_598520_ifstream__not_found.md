---
title: "ifstream  not found"
date: 2007-10-31
forum: Programming Talk
---

### Post by nbo10 on 2007-10-31
I just started to use ubuntu. Soooo much better than XP.

I can get a basic Hello world program to compile but when  I add "#include <ifstream>" so that I can read file I get the following: "error: ifstream: No such file or Dir"

I'm using gedit and command line to compile. How do I fix this? Thanks

---

### Post by Paul820 on 2007-10-31
It's > #include <fstream>

Inside your program you use ifstream to read the file and ofstream to write to it.

---

