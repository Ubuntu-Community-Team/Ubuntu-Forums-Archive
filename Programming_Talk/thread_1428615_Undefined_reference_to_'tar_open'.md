---
title: "Undefined reference to 'tar_open'"
date: 2010-03-13
forum: Programming Talk
---

### Post by y50a7XpWRH66IV on 2010-03-13
Hi everyone,

Does anyone know how to compile a program that uses libtar successfully?

Currently, I have the following:
```

#include <config.h>
#include <libtar.h>
#include <string.h>
#include <fcntl.h>

void main()
{
	TAR *p_tar;

	char *file ="/usr/home/user/test.tar";

	tar_open ( &p_tar, file, NULL, O_RDONLY, 0644, TAR_GNU );
}

```

When compiling in KDevelop, I get the following error:
```

Undefined reference to 'tar_open'

```

There is, however, no errors for: TAR *p_tar;

I have added libtar to my compiler flags:
```

-O0 -g3 $(pkg-config --cflags --libs libtar)

```

In addition, I have created a libtar.pc file in /usr/lib/pkgconfig

Here is the libtar.pc file I have created:
```

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
includedir=${prefix}/include

Name: libtar
Description: libtar
Version: 1.2.11
URL: http://www.feep.net/libtar/

Libs: -L${libdir}/libtar.so

Cflags: -I${includedir}

```

Does anyone know how to fix this?

Cheers:)

---

### Post by soltanis on 2010-03-13
Usually when I link external libraries I find they don't have "lib" in front of them, as in,

```

gcc -c crunch.c -lm

```
Links the Math library.

I don't know about the long --libs form but have you tried -ltar?

If your error is in the linker phase then chances are the library isn't being picked up properly.

---

### Post by y50a7XpWRH66IV on 2010-03-13
Thanks! That did the trick.

I had to compile with gtk and gmodule so I was under the impression I had to use pkg-config.

This did the trick:
```

-O0 -g3 $(pkg-config --cflags --libs gtk+-2.0 gmodule-2.0) -ltar

```

---

