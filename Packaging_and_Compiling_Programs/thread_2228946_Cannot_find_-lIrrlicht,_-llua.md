---
title: "Cannot find -lIrrlicht, -llua"
date: 2014-06-10
forum: Packaging and Compiling Programs
---

### Post by mrlak55 on 2014-06-10
Hello,
I am trying to build this game ([https://github.com/soarqin/ygopro](https://github.com/soarqin/ygopro)). I have installed Irrlicht and Lua, but linker gives me these errors:
```

/usr/bin/ld: cannot find -lIrrlicht
/usr/bin/ld: cannot find -llua
```
There are some solutions on StackOverflow ([http://stackoverflow.com/questions/16710047/usr-bin-ld-cannot-find-lnameofthelibrary](http://stackoverflow.com/questions/16710047/usr-bin-ld-cannot-find-lnameofthelibrary)), but answers there don't work for me because I don't have lua.so or irrlicht.so files in /usr/lib/ (or anywhere else, as far as I know). I installed Lua with apt-get install, so I expected at least that to work - but it doesn't. How do I fix this?

Any help is appreciated.


EDIT:
It seems that I haven't had libraries installed. Fixed now.

---

