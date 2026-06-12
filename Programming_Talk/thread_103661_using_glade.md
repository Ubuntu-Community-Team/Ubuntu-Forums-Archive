---
title: "using glade"
date: 2005-12-14
forum: Programming Talk
---

### Post by rock freak on 2005-12-14
```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0. 0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the PACKAGE_CFLAGS and PACKAGE_LIBS environment variab les
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

i get this error when i run the autogen on blade 2 any ideas guys?

---

### Post by fct on 2005-12-14
Install this package: libgtk2.0-dev

---

### Post by rock freak on 2005-12-14
are! the only one i hadnt installed lol ill tell ya if it works:)

---

### Post by rock freak on 2005-12-14
excellent cheers any one got any good tutorials for it at all??

just done the [www.writelinux.com/glade](www.writelinux.com/glade) one :D

---

### Post by fct on 2005-12-15
You should check libglade. It allows you to load the interface definition file from your code, and thus you don't need to recompile when you change the interface.

Tutorial here:

[http://www.micahcarrick.com/v2/content/category/1/5/3/](http://www.micahcarrick.com/v2/content/category/1/5/3/)

---

