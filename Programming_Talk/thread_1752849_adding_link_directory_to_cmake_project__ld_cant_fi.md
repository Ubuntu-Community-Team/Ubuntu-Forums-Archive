---
title: "adding link directory to cmake project : ld cant find lib"
date: 2011-05-08
forum: Programming Talk
---

### Post by saibaggins on 2011-05-08
my cmake knowledge is fairly minimal. Now I want to link against a
external library when i build my project.

from the documentation i think it should be possible to do:

LINK_DIRECTORIES( ${LINK_DIRECTORIES} /absPath/libtourtre/)

but i get lots of undefined references. I have tried a simple non-cmake
example and linked it with -L/absPath/libtourtre/ -ltourtre and it
works fine so i'm at a loss where i'm going wrong.

further note:
if i put link_directories after add executable i dont get undefined
references, just
/usr/bin/ld: cannot find -ltourtre

there must be a simple solution for this but i can't seem to find
despite trawling the web...

---

