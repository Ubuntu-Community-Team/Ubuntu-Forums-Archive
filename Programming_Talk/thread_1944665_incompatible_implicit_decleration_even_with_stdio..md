---
title: "incompatible implicit decleration even with stdio.h"
date: 2012-03-21
forum: Programming Talk
---

### Post by hasush on 2012-03-21
I am running Ubuntu 10.10 live in Windows 7 with i7.

**My gcc version:**
gcc -v
Using built-in specs.
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.4.4-14ubuntu5.1' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.4 --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
[B]gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5.1) 

code:
[/B]#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <strings.h>
int main()
{
    printf("\nhello\n");
    return 0;
}

[B]error:
[/B]gcc -o hello hello.chello.c: In function &#8216;main&#8217;:
hello.c:5: warning: incompatible implicit declaration of built-in function &#8216;printf'

Thank you in advance.

---

### Post by nothingspecial on 2012-03-23
*Thread moved to **Programming Talk**.*

---

### Post by lkraemer on 2012-03-23
Google is your friend!

Google finds:
[http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html](http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html)

lk

---

### Post by Zugzwang on 2012-03-23
Ensure that the package "build-essential" installed. Also check that there is no file named "stdio.h" in the directory that you are compiling from.

---

### Post by trent.josephsen on 2012-03-23
@lkramer: Not C.  Also irrelevant to OP's problem, unless you're seeing something I'm not.

@OP:  The code you posted is not the code you compiled.  Lose the unnecessary #includes (all of them but <stdio.h>), recompile it, and post again if you still get a warning.

---

