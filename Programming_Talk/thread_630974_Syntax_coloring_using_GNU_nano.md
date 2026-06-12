---
title: "Syntax coloring using GNU nano"
date: 2007-12-03
forum: Programming Talk
---

### Post by tennvolsmb on 2007-12-03
Okay so i've read all the other posts and could someone please break this down for me.. I program in C++ and just learned about syntax highlighting so I thought it would be helpful... can someone break it down for me and explain it in detail... please be nice and am just a beginner!

---

### Post by jpkotta on 2007-12-04
```
for i in /usr/share/nano/*nanorc ; do echo "include \"$i\"" ; done >> ~/.nanorc

```

There are a bunch of nano config files in  /usr/share/nano/, so we tell nano to look at them with the include directive (it is roughly the same as #include from C/C++).  

Additional help:
```
man nanorc
```

Personally, I prefer joe to nano if you want a simple editor.  It has a pico mode which is used when you run it as "jpico" (nano is a pico clone).  I like [X]Emacs even more, mainly for the indentation engine.

---

