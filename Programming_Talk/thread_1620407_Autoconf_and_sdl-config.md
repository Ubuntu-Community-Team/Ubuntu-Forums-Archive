---
title: "Autoconf and sdl-config"
date: 2010-11-13
forum: Programming Talk
---

### Post by dawwin on 2010-11-13
I must check, whether SDL library is installed before compilation, but I don't know how. 
Usually I use something like this
```
AC_CHECK_LIB(ncurses, initscr, , AC_MSG_ERROR(ncurses - library not found))
```But SDL has got special script (sdl-config), so I don't know how to check, whether this library is installed. Can anyone help me?

---

