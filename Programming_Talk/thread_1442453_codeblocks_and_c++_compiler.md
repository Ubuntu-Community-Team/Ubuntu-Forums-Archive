---
title: "code::blocks and c++ compiler"
date: 2010-03-30
forum: Programming Talk
---

### Post by crlang13 on 2010-03-30
Hey there, I've used code::blocks in windows as an IDE for c++ with no problems.

I tried compiling a program on an Ubuntu version than I just got straight from the software center.  I haven't added any other compilers or anything to my machine.  When I first opened code blocks, it asked which compiler I wanted to use, it looked like all I had was the GNU GCC compiler.

When I go to compile, I get an error:

/bin/sh: g++: not found

I took a look in synaptic, and I'm not sure if the GNU GCC compiler supports C++ out of the box (as I said, I haven't added anything).  Or is there something else I have to download?

---

### Post by deer dance on 2010-03-30
```
sudo apt-get install g++
```

---

### Post by crlang13 on 2010-03-30
thanks deer dance :p

that's the package that I thought it would be, but I didn't want to go on a wild goose chase.

---

