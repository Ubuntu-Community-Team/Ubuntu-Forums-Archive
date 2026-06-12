---
title: "Is it possible to linking libncurses5 library with mingw on Linux to Windows?"
date: 2015-08-18
forum: Programming Talk
---

### Post by flaymond on 2015-08-18
I'm looking and searching for the answers by the Google, but none of them are the exact answer I want to find. Anyone have an experience or ideas to do this? I'm just doing this for fun, and not for money or commercial things, just wanna see if i686-w64-mingw32-gcc can statically link libncurses5 library with it. Thanks for helping out!


**** I also tried *** -

```
 i686-w64-mingw32-gcc myfile.c -o myfile.exe -lncurses 
```

-- That just don't work

---

### Post by flaymond on 2015-08-20
After a few research I did, there's no easy way to linking libraries on Linux, since it will require .dll for Windows platform. Closing this thread.

---

