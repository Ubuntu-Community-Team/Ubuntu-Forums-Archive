---
title: "How to compile a windows program in Linux"
date: 2009-05-11
forum: Programming Talk
---

### Post by camper365 on 2009-05-11
I am trying to write a program using Linux, and compile it into a Windows program.
How do I do that.
I know it's called cross-compiling, and I have looked a mingw, but I couldn't find anything there.

---

### Post by zolistir87 on 2009-05-11
I think you need a windows compiler for that.

---

### Post by The Cog on 2009-05-11
[http://ubuntuforums.org/showthread.php?t=1141290](http://ubuntuforums.org/showthread.php?t=1141290)

To compile for Linux is:
```
gcc -Wall -o foo foo.c
```

To compile for windows is:
```
i586-mingw32msvc-gcc -Wall -o foo.exe foo.c
```

---

### Post by camper365 on 2009-05-13
thx

---

