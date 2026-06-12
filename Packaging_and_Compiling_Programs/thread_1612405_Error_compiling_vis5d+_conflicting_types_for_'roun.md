---
title: "Error compiling vis5d+: conflicting types for 'round'"
date: 2010-11-03
forum: Packaging and Compiling Programs
---

### Post by KIAaze on 2010-11-03
Hi,

I'm trying to compile vis5d+ on Ubuntu 10.10: [http://vis5d.sourceforge.net/](http://vis5d.sourceforge.net/)
configure runs successfully, but make fails with:
```
cc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O3 -fomit-frame-pointer -malign-double -c api.c -MT api.lo -MD -MP -MF .deps/api.TPlo  -fPIC -DPIC -o api.o
In file included from api.c:89:
misc.h:40: error: conflicting types for 'round'

```

Some extracts from the source code:

./src/api.c:
```

...
#include <math.h>
...
#include "misc.h"
...

```

./src/misc.h:
```

...
extern float round( float x );
...

```

./src/misc.c:
```

...
#include <math.h>
...
float round( float x )
{
   float base, fudge;
   int temp;

   for (base=1000000.0; fabs(x/base)<1.0 && base>0.000001; base/=10.0);

   fudge = (x>0.0) ? 0.5 : -0.5;
   temp = (int) (x/base + fudge);
   return temp * base;
}
...

```

I tried both the latest stable 1.2.1 version, as well as the 1.3.0 beta version.

I'm attaching the config.log and the outputs of configure and make for both releases.

```
$ gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.4.4-14ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.4 --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5)
```

---

### Post by KIAaze on 2010-11-03
Problem solved the ugly way by renaming the "round" function in all source files to "custom_round".
After that I got some fortran compile errors.
This was solved by using:
```
./configure --disable-fortran
```

I probably lost some functionality that way, but at least I can start vis5d now.

---

