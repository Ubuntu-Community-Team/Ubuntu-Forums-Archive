---
title: "Why D language executables produced with gdc4.8 is big (9.8 MiB)"
date: 2015-06-27
forum: Programming Talk
---

### Post by flaymond on 2015-06-27
Hi! After having fun with D programming, I'm just curious why D executables are big size. From my experience in C, I found the executable become bigger when I linking from a lot of libraries at a time or in  number crunching tasks(there's more, just don't want list all of them in here). Anyway, D executable with a simple hello world example, still producing 9.8 MiB size of executable. Is there anyone programming with D, has the same problem/feature with me, or it's just me. Also, anyone know how to reduce size of this executable, if not why it's big? (luckily the runtime is as almost fast as native C++ code). If dmd compiler, produced more smaller sizes, I think it's something wrong with gdc or it's just my installation. The support for D and questions is still lacking, need to open a new thread for it. Thanks! ;)


# Is it all about the garbage collecting things? That cause this disadvantage (especially on a PC that has low hard disk space)?

---

