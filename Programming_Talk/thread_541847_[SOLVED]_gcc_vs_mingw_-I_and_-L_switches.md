---
title: "[SOLVED] gcc vs mingw -I and -L switches"
date: 2007-09-03
forum: Programming Talk
---

### Post by samjh on 2007-09-03
Can anyone explain to me why I don't need to specify -I and -L options when compiling a Linux program with gcc using the -c switch, yet it is necessary to specify -I and -L options when using i586-mingw32msvc-gcc's -c switch?

EDIT:

Just realised that the linux headers were in the system's include directory, but the win32 headers were not!  Captain obvious to the rescue! :p

---

