---
title: "dynamically linked library"
date: 2011-08-15
forum: Programming Talk
---

### Post by tbastian on 2011-08-15
I'm writing some software that mainly revolves around plotting data in semi-realtime, so I ended up writing my own plotting library. One of my colleagues also has a good application for this library, so I compiled it as a separate package/library using libtool. When I install the appropriate files to the appropriate place, When I try to link with it like I would any other library, the compiler just spits out "undefined reference" errors to all my library calls.

I installed the files to the following places:
```

headers -> /usr/include
libplot.so.0.0.0 -> /usr/lib # all the sym links too
libplot.pc -> /usr/lib/pkgconfig

```

this is my libplot.pc
```

prefix=/usr
exec_prefix=${prefix}
libdir=/usr/lib
includedir=/usr/include

Name: libplot
Description: plotting library with timehistory plots, strip plots, XY plots and track plots
Version: 0.1-2

Requires.private: gtk+-2.0 >= 2.18.3	cairo >= 1.8.8
Libs: -L${libdir}
Cflags: -I${includedir}/libplot

```

When I put ```
/usr/lib/libplot.so.0.0.0
``` in the flag "program_LDADD", it compiles fine. How can I get `pkg-config --libs` to properly link everything?

---

### Post by Bachstelze on 2011-08-15
Are you compiling with -lplot?

---

### Post by tbastian on 2011-08-15
That did it! thanks a lot!

---

