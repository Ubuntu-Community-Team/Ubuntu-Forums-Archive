---
title: "error: tp-connmgr.h: No such file or directory"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by deepdhan on 2008-10-10
Hi,
 I have installed telepathy and gabble.. and i m trying to write a c program with "#include <tp-connmgr.h>" line.. 

when i do:
gcc testTelepathy.c `pkg-config --cflags --libs libtelepathy` 
it gives me

testTelepathy.c:2:24: error: tp-connmgr.h: No such file or directory


i have set my PKG_CONFIG_PATH to /usr/local/lib/pkgconfig 
where /usr/local/lib/pkgconfig contains 
libtelepathy.pc  telepathy-glib.pc  telepathy-glib-unstable.pc


and i have tp-connmgr.h in /usr/local/include/telepathy-1.0/libtelepathy/ 


Can anyone help me whats the problem???

---

### Post by iaculallad on 2008-10-10
Try copying tp-connmgr.h to the /usr/include directory.

---

### Post by deepdhan on 2008-10-10
i have installed that telepathy and it placed all the libraries and include files in /usr/local/include directory.. now just copying one file mite not help..

---

