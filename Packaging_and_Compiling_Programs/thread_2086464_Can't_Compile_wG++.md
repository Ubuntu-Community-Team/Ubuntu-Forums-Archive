---
title: "Can't Compile w/G++"
date: 2012-11-21
forum: Packaging and Compiling Programs
---

### Post by Tk007LwZFJW5ej on 2012-11-21
This is my first time compiling .cpp on linux. My files are main.cpp, linkedlist.cpp, and linkedlist.h. I tried

```
g++ main.cpp linkedlist.cpp
```

and get the bizarre message

```
bash: /usr/bin/gpp: No such file or directory
```.

gpp is a "general-purpose preprocessor" that is not installed.  Shouldn't I be able to compile without this?

---

### Post by Tk007LwZFJW5ej on 2012-11-21
whoops, nevermind. Gcc was set as an alias of gpp.

---

