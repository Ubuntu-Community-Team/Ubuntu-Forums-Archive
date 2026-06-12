---
title: "pkg-config gtk+3.0"
date: 2012-05-20
forum: Packaging and Compiling Programs
---

### Post by tomdesert on 2012-05-20
Dear All,

I am changing over to GTK3 and have upgraded to 11.10. So far so good. When trying to compile a program I get an error message saying that pkg-config  cannot find gtk+3.0 and I might add it to the PKG_CONFIG_PATH.

gtk+3.0.pc is in /usr/lib/pkgconfig directory. 

When I query pkg-config defaults it tells me that /usr/lib/pkgconfig is part of the search path.

What can be wrong? Someone an idea?

regards
Thomas

---

### Post by MadCow108 on 2012-05-21
its gtk+-3.0 not gtk+3.0:
```
# pkg-config --modversion gtk+-3.0
3.2.0

```

see
```
pkg-config --list-all | grep gtk
```

---

