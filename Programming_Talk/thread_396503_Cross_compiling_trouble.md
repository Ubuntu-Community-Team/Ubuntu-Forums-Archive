---
title: "Cross compiling trouble"
date: 2007-03-29
forum: Programming Talk
---

### Post by kaamos on 2007-03-29
Hello,

I'm trying to cross compile gtk for windows from ubuntu. I know there a gtk binary packages for windows, I'm just learning how to do this. So, I have a working cross compile enviroment (compiled a project using clanlib with it successfully), but I'm now having some problems with glib. Glib compiles but I have trouble linking programs with it.

Test program:
```

#include <glib.h>

int main(void)
{
    g_listenv();

    return 0;
}

```
Compiling with
```

i586-mingw32msvc-gcc -I/usr/i586-mingw32msvc/include/glib-2.0 -I/usr/i586-mingw32msvc/lib/glib-2.0/include  -L/usr/i586-mingw32msvc/lib -lgobject-2.0 -lglib-2.0 -lintl -liconv test.c

```
Linking fails with this error (note the underscore before g_listenv)
```

/tmp/ccYpY4KG.o:mytest.c:(.text+0x2b): undefined reference to `_g_listenv'
collect2: ld returned 1 exit status

```

Any ideas what I'm doing wrong?

---

