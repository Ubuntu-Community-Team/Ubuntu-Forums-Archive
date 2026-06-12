---
title: "Qt programs not running... have i missed something?"
date: 2010-07-27
forum: Programming Talk
---

### Post by Guitar-maniac on 2010-07-27
Recently started to programming qt to try something new and interesting, i compiled them and i have the .pro file in the folder.
But i cant seem to get in running? I did simple HelloWorld as a test named it to exr1.cpp. Them compiled it into exr1.o(?) as instructions said. That's as far as i got, i followed guides but i didn't work.

I was in the right folder when trying to run it, i have little knowledge abt C++ and Java, se i'm not complete noob for compiling/running programs through the command line.

---

### Post by dwhitney67 on 2010-07-27
From what I recall, these are the steps:
```

qmake exr1.pro

make

./exr1

```
Of course, substitute the name of the .pro and executable files above if they differ from yours.

---

### Post by Guitar-maniac on 2010-07-27
Thanks, that did it! Was missing the make command in between.

---

