---
title: "compyling librtp"
date: 2009-02-02
forum: Programming Talk
---

### Post by nenjordi on 2009-02-02
Hi
FYI
If you are trying to compile librtp in hardy, this interests you if not I'm sorry :)

In order to compile, change in configure.in  AM_PATH_GLIB by AM_PATH_GLIB_2_0

and copy /usr/share/libtool/ltmain.sh into librtp dir

with that you should be able to compile :D

---

