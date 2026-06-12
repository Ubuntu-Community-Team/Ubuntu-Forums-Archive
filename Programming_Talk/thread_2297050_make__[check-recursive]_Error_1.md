---
title: "make: *** [check-recursive] Error 1"
date: 2015-09-30
forum: Programming Talk
---

### Post by patrick105 on 2015-09-30
Getting this error while trying to install Epson Photo 280 printer driver:

```
patrick@pat-ubuntu:~/pips-common-3.0$ sudo make checkMaking check in m4
make[1]: Entering directory `/home/patrick/pips-common-3.0/m4'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/patrick/pips-common-3.0/m4'
Making check in intl
make[1]: Entering directory `/home/patrick/pips-common-3.0/intl'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/patrick/pips-common-3.0/intl'
Making check in libltdl
make[1]: Entering directory `/home/patrick/pips-common-3.0/libltdl'
make[1]: Leaving directory `/home/patrick/pips-common-3.0/libltdl'
Making check in Core
make[1]: Entering directory `/home/patrick/pips-common-3.0/Core'
Making check in ekpd
make[2]: Entering directory `/home/patrick/pips-common-3.0/Core/ekpd'
make[2]: Nothing to be done for `check'.
make[2]: Leaving directory `/home/patrick/pips-common-3.0/Core/ekpd'
Making check in libcap
make[2]: Entering directory `/home/patrick/pips-common-3.0/Core/libcap'
make[2]: Nothing to be done for `check'.
make[2]: Leaving directory `/home/patrick/pips-common-3.0/Core/libcap'
Making check in libutils
make[2]: Entering directory `/home/patrick/pips-common-3.0/Core/libutils'
make[2]: Nothing to be done for `check'.
make[2]: Leaving directory `/home/patrick/pips-common-3.0/Core/libutils'
Making check in pips-filter
make[2]: Entering directory `/home/patrick/pips-common-3.0/Core/pips-filter'
/bin/bash ../../libtool --mode=link gcc -DLOCALE_PATH=\"/usr/local/share/locale\" -D_LPR_DIRECT -g -O2 -Wall   -o pips-filter  debug.o pfatt.o pfimg.o pfpng.o pips-filter.o pngfilter.o rawfilter.o -lstdc++ ../../libltdl/libltdlc.la -lxml2 ../../Core/libutils/libpips-utils.la -lpthread 
gcc -DLOCALE_PATH=\"/usr/local/share/locale\" -D_LPR_DIRECT -g -O2 -Wall -o .libs/pips-filter debug.o pfatt.o pfimg.o pfpng.o pips-filter.o pngfilter.o rawfilter.o  -lstdc++ ../../libltdl/.libs/libltdlc.al -lxml2 ../../Core/libutils/.libs/libpips-utils.so -ldl -lpthread -Wl,--rpath -Wl,/usr/local/lib
pfimg.o: In function `set_raster':
/home/patrick/pips-common-3.0/Core/pips-filter/pfimg.c:1253: undefined reference to `floor'
pfimg.o: In function `load_image_out':
/home/patrick/pips-common-3.0/Core/pips-filter/pfimg.c:843: undefined reference to `floor'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlFreeDoc'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlGetProp'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlStrcmp'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlNodeListGetString'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlParseFile'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlFree'
../../Core/libutils/.libs/libpips-utils.so: undefined reference to `xmlDocGetRootElement'
collect2: error: ld returned 1 exit status
make[2]: *** [pips-filter] Error 1
make[2]: Leaving directory `/home/patrick/pips-common-3.0/Core/pips-filter'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/patrick/pips-common-3.0/Core'
make: *** [check-recursive] Error 1



```

Any help appreciated.

---

### Post by Rocket2DMn on 2015-10-01
It looks like possibly two problems.

First, I'll assume the undefined references to xml... functions are from libxml2.  Try installing libxml2 and libxml2-dev:
```

sudo apt-get install libxml2 libxml2-dev

```
Then try again.

Second, if it still doesn't work (you still get "undefined reference to `floor'") - they didn't like against libm in their Makefile.  It's an easy mistake to make as some systems link to it automatically.  So there should be a "-lm" after "-ldl -lpthread".  You might try adding it manually.

---

### Post by patrick105 on 2015-10-01
> **Rocket2DMn said:**
> It looks like possibly two problems.

First, I'll assume the undefined references to xml... functions are from libxml2.  Try installing libxml2 and libxml2-dev:
```

sudo apt-get install libxml2 libxml2-dev

```
Then try again.

Second, if it still doesn't work (you still get "undefined reference to `floor'") - they didn't like against libm in their Makefile.  It's an easy mistake to make as some systems link to it automatically.  So there should be a "-lm" after "-ldl -lpthread".  You might try adding it manually.


I already had the above two libraries installed so that didn't help.  I'm still getting undefined references to xml's. Additionally, in the makefile, there is "-lm" after "-lpthread" but there's no "-ldl" anywhere.  Any thoughts?

---

### Post by steeldriver on 2015-10-02
It seems to be a link order issue - you can see from the gcc command line that it is linking libxml2 before libpips-utils.so

```

gcc -DLOCALE_PATH=\"/usr/local/share/locale\" -D_LPR_DIRECT -g -O2 -Wall -o .libs/pips-filter \
debug.o pfatt.o pfimg.o pfpng.o pips-filter.o pngfilter.o rawfilter.o  \
-lstdc++ ../../libltdl/.libs/libltdlc.al **-lxml2 ../../Core/libutils/.libs/libpips-utils.so** -ldl -lpthread -Wl,--rpath -Wl,/usr/local/lib

```

---

### Post by patrick105 on 2015-10-02
> **steeldriver said:**
> It seems to be a link order issue - you can see from the gcc command line that it is linking libxml2 before libpips-utils.so

```

gcc -DLOCALE_PATH=\"/usr/local/share/locale\" -D_LPR_DIRECT -g -O2 -Wall -o .libs/pips-filter \
debug.o pfatt.o pfimg.o pfpng.o pips-filter.o pngfilter.o rawfilter.o  \
-lstdc++ ../../libltdl/.libs/libltdlc.al **-lxml2 ../../Core/libutils/.libs/libpips-utils.so** -ldl -lpthread -Wl,--rpath -Wl,/usr/local/lib

```


I'm new to linux so I don't really know what that means.  What should I do?

---

### Post by steeldriver on 2015-10-02
You could edit /home/patrick/pips-common-3.0/Core/pips-filter and change

```

pips_filter_LDADD = \
        -lstdc++ \
        ${top_builddir}/libltdl/libltdlc.la \
[B]        -lxml2 \
        $(top_srcdir)/Core/libutils/libpips-utils.la
[/B]
```

to

```

pips_filter_LDADD = \
        -lstdc++ \
        ${top_builddir}/libltdl/libltdlc.la \
[B]        $(top_srcdir)/Core/libutils/libpips-utils.la \
        -lxml2 \
[/B]        -lm

```

You will probably need to do the same (apart from the addition of the math library -lm, which seems to be an issue only for the Core/pips-filter component) to the corresponding _LDADD variables in all the other subordinate Makefiles.

However after doing all that there were other errors... at which point I gave up.

---

