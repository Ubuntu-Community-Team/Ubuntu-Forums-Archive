---
title: "Compiling Apache 2.2: Make dieing horribly in a bloody mess"
date: 2008-01-03
forum: Packaging and Compiling Programs
---

### Post by irkengir on 2008-01-03
Hey folks.

I'm trying to get Apache 2.2 installed so I can use mod_proxy_balance.

I'm using this configure line:
```

./configure -q --prefix=/usr/local/apache2 \
            --enable-mods-shared=all \
            --enable-deflate \           
            --enable-proxy \
            --enable-proxy-balancer \
            --enable-proxy-http \
            --with-mpm=prefork

```

configure runs successfully but make dies with this information:

```
/usr/bin/ld: /usr/local/lib/libz.a(crc32.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libz.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[4]: *** [mod_deflate.la] Error 1
make[4]: Leaving directory `/usr/src/httpd-2.2.6/modules/filters'
make[3]: *** [shared-build-recursive] Error 1
make[3]: Leaving directory `/usr/src/httpd-2.2.6/modules/filters'
make[2]: *** [shared-build-recursive] Error 1
make[2]: Leaving directory `/usr/src/httpd-2.2.6/modules'
make[1]: *** [shared-build-recursive] Error 1
make[1]: Leaving directory `/usr/src/httpd-2.2.6'
make: *** [all-recursive] Error 1
```

Any ideas? 
I'm running all the commands as root.

---

### Post by irkengir on 2008-01-10
Ahh, the solution was "apt-get upgrade" I guess some of the build tools were out of date.

---

### Post by irkengir on 2008-01-10
Also I changed --enable-deflate to --disable-deflate.

---

