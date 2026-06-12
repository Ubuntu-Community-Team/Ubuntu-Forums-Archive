---
title: "'make' error"
date: 2011-11-26
forum: Packaging and Compiling Programs
---

### Post by searchfgold6789 on 2011-11-26
Hi,
I'm getting this strange error when compiling gstreamer 0.6.5 - I saw no other way to get this version of the program other than from source. When I ./configure all things go ok, but when I do the make command this is the output:```
user@computer:~/gstreamer/gstreamer-0.6.5$ make
make  all-recursive
make[1]: Entering directory `/home/user/gstreamer/gstreamer-0.6.5'
Making all in include
make[2]: Entering directory `/home/user/gstreamer/gstreamer-0.6.5/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/user/gstreamer/gstreamer-0.6.5/include'
Making all in gst
make[2]: Entering directory `/home/user/gstreamer/gstreamer-0.6.5/gst'
make  all-recursive
make[3]: Entering directory `/home/user/gstreamer/gstreamer-0.6.5/gst'
Making all in parse
make[4]: Entering directory `/home/user/gstreamer/gstreamer-0.6.5/gst/parse'
make  all-am
make[5]: Entering directory `/home/user/gstreamer/gstreamer-0.6.5/gst/parse'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/user/gstreamer/gstreamer-0.6.5/gst/parse'
make[4]: Leaving directory `/home/user/gstreamer/gstreamer-0.6.5/gst/parse'
Making all in registries
make[4]: Entering directory `/home/user/gstreamer/gstreamer-0.6.5/gst/registries'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/user/gstreamer/gstreamer-0.6.5/gst/registries'
Making all in .
make[4]: Entering directory `/home/user/gstreamer/gstreamer-0.6.5/gst'
if /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -D_GNU_SOURCE -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I/usr/include/libxml2   -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include   -I..  -Wall -DGST_DISABLE_DEPRECATED -g -I../libs -I../include -DG_LOG_DOMAIN=g_log_domain_gstreamer -DGST_CACHE_DIR=\""/usr/local/var/cache/gstreamer-0.6"\"  -g -O2 -MT libgstreamer_0.6_la-gst.lo -MD -MP -MF ".deps/libgstreamer_0.6_la-gst.Tpo" \
      -c -o libgstreamer_0.6_la-gst.lo `test -f 'gst.c' || echo './'`gst.c; \
    then mv -f ".deps/libgstreamer_0.6_la-gst.Tpo" ".deps/libgstreamer_0.6_la-gst.Plo"; \
    else rm -f ".deps/libgstreamer_0.6_la-gst.Tpo"; exit 1; \
    fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_GNU_SOURCE -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/libxml2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I.. -Wall -DGST_DISABLE_DEPRECATED -g -I../libs -I../include -DG_LOG_DOMAIN=g_log_domain_gstreamer -DGST_CACHE_DIR=\"/usr/local/var/cache/gstreamer-0.6\" -g -O2 -MT libgstreamer_0.6_la-gst.lo -MD -MP -MF .deps/libgstreamer_0.6_la-gst.Tpo -c gst.c  -fPIC -DPIC -o .libs/libgstreamer_0.6_la-gst.o
gst.c: In function 'init_popt_callback':
gst.c:602:7: warning: pointer targets in passing argument 2 of 'parse_number' differ in signedness [-Wpointer-sign]
gst.c:343:1: note: expected 'guint32 *' but argument is of type 'gint *'
gst.c:606:7: warning: pointer targets in passing argument 2 of 'parse_number' differ in signedness [-Wpointer-sign]
gst.c:343:1: note: expected 'guint32 *' but argument is of type 'gint *'
gst.c:610:7: warning: pointer targets in passing argument 2 of 'parse_number' differ in signedness [-Wpointer-sign]
gst.c:343:1: note: expected 'guint32 *' but argument is of type 'gint *'
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_GNU_SOURCE -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/libxml2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I.. -Wall -DGST_DISABLE_DEPRECATED -g -I../libs -I../include -DG_LOG_DOMAIN=g_log_domain_gstreamer -DGST_CACHE_DIR=\"/usr/local/var/cache/gstreamer-0.6\" -g -O2 -MT libgstreamer_0.6_la-gst.lo -MD -MP -MF .deps/libgstreamer_0.6_la-gst.Tpo -c gst.c -o libgstreamer_0.6_la-gst.o >/dev/null 2>&1
if /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -D_GNU_SOURCE -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I/usr/include/libxml2   -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include   -I..  -Wall -DGST_DISABLE_DEPRECATED -g -I../libs -I../include -DG_LOG_DOMAIN=g_log_domain_gstreamer -DGST_CACHE_DIR=\""/usr/local/var/cache/gstreamer-0.6"\"  -g -O2 -MT libgstreamer_0.6_la-gstenumtypes.lo -MD -MP -MF ".deps/libgstreamer_0.6_la-gstenumtypes.Tpo" \
      -c -o libgstreamer_0.6_la-gstenumtypes.lo `test -f 'gstenumtypes.c' || echo './'`gstenumtypes.c; \
    then mv -f ".deps/libgstreamer_0.6_la-gstenumtypes.Tpo" ".deps/libgstreamer_0.6_la-gstenumtypes.Plo"; \
    else rm -f ".deps/libgstreamer_0.6_la-gstenumtypes.Tpo"; exit 1; \
    fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_GNU_SOURCE -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/libxml2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I.. -Wall -DGST_DISABLE_DEPRECATED -g -I../libs -I../include -DG_LOG_DOMAIN=g_log_domain_gstreamer -DGST_CACHE_DIR=\"/usr/local/var/cache/gstreamer-0.6\" -g -O2 -MT libgstreamer_0.6_la-gstenumtypes.lo -MD -MP -MF .deps/libgstreamer_0.6_la-gstenumtypes.Tpo -c gstenumtypes.c  -fPIC -DPIC -o .libs/libgstreamer_0.6_la-gstenumtypes.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_GNU_SOURCE -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/libxml2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I.. -Wall -DGST_DISABLE_DEPRECATED -g -I../libs -I../include -DG_LOG_DOMAIN=g_log_domain_gstreamer -DGST_CACHE_DIR=\"/usr/local/var/cache/gstreamer-0.6\" -g -O2 -MT libgstreamer_0.6_la-gstenumtypes.lo -MD -MP -MF .deps/libgstreamer_0.6_la-gstenumtypes.Tpo -c gstenumtypes.c -o libgstreamer_0.6_la-gstenumtypes.o >/dev/null 2>&1
if /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -D_GNU_SOURCE -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I/usr/include/libxml2   -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include   -I..  -Wall -DGST_DISABLE_DEPRECATED -g -I../libs -I../include -DG_LOG_DOMAIN=g_log_domain_gstreamer -DGST_CACHE_DIR=\""/usr/local/var/cache/gstreamer-0.6"\"  -g -O2 -MT libgstreamer_0.6_la-gstmemchunk.lo -MD -MP -MF ".deps/libgstreamer_0.6_la-gstmemchunk.Tpo" \
      -c -o libgstreamer_0.6_la-gstmemchunk.lo `test -f 'gstmemchunk.c' || echo './'`gstmemchunk.c; \
    then mv -f ".deps/libgstreamer_0.6_la-gstmemchunk.Tpo" ".deps/libgstreamer_0.6_la-gstmemchunk.Plo"; \
    else rm -f ".deps/libgstreamer_0.6_la-gstmemchunk.Tpo"; exit 1; \
    fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -D_GNU_SOURCE -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/libxml2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I.. -Wall -DGST_DISABLE_DEPRECATED -g -I../libs -I../include -DG_LOG_DOMAIN=g_log_domain_gstreamer -DGST_CACHE_DIR=\"/usr/local/var/cache/gstreamer-0.6\" -g -O2 -MT libgstreamer_0.6_la-gstmemchunk.lo -MD -MP -MF .deps/libgstreamer_0.6_la-gstmemchunk.Tpo -c gstmemchunk.c  -fPIC -DPIC -o .libs/libgstreamer_0.6_la-gstmemchunk.o
In file included from gstmemchunk.c:25:0:
gsttrashstack.h: In function 'gst_mem_chunk_alloc':
gsttrashstack.h:103:3: error: PIC register clobbered by 'ebx' in 'asm'
make[4]: *** [libgstreamer_0.6_la-gstmemchunk.lo] Error 1
make[4]: Leaving directory `/home/user/gstreamer/gstreamer-0.6.5/gst'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/user/gstreamer/gstreamer-0.6.5/gst'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/user/gstreamer/gstreamer-0.6.5/gst'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/gstreamer/gstreamer-0.6.5'
make: *** [all] Error 2

```These lines catch my attention:```
 In file included from gstmemchunk.c:25:0:
gsttrashstack.h: In function 'gst_mem_chunk_alloc':
gsttrashstack.h:103:3: error: PIC register clobbered by 'ebx' in 'asm'
```What is going on?! Also, there's an interesting warning when I do ./configure, but it goes ahead anyway:```
configure: WARNING: Sissy ! By asking to not build the tests known to fail, you hereby waive your right to customer support.  If you do not agree with this EULA, please press Ctrl-C before the next line is printed.  By allowing the next line to be printed, you expressly acknowledge your acceptance of this EULA.
```

---

### Post by SevenMachines on 2011-11-26
> **searchfgold6789 said:**
> Hi,
I'm getting this strange error when compiling gstreamer 0.6.5 - I saw no other way to get this version of the program other than from source.  I would give the obligatory warning first. That version is almost 8 years old, a lifetime in linux terms, don't use it!

```
 gsttrashstack.h:103:3: error: PIC register clobbered by 'ebx' in 'asm'
```I'm guessing some pushing and popping of ebx would be required, I'll look up something 
```
configure: WARNING: Sissy ! By asking to not build the tests known to fail, you hereby waive your right to customer support.  If you do not agree with this EULA, please press Ctrl-C before the next line is printed.  By allowing the next line to be printed, you expressly acknowledge your acceptance of this EULA
```Programmer humour :)

---

### Post by SevenMachines on 2011-11-26
```
 __asm__ __volatile__ (
    "  pushl %%ebx;             \n\t"
    "  testl %%eax, %%eax;      \n\t"    /* if (head == NULL) return */
    "  jz 20f;                  \n\t"
    "10:                        \n\t"
    "  movl (%%eax), %%ebx;     \n\t"    /* take value pointed to by head (head->next) */
    "  movl %%edx, %%ecx;       \n\t"    /* take counter */
    "  incl %%ecx;              \n\t"    /* and increment */
    SMP_LOCK "cmpxchg8b %1;     \n\t"    /* if eax:edx == *stack, move ebx:ecx to *stack,
                     * else *stack is moved into eax:edx again... */
    "  jz 20f;                  \n\t"   /* success */
    "  testl %%eax, %%eax;      \n\t"   /* if (head == NULL) return */
    "  jnz 10b;                 \n\t"   /* else we retry */
    "20:                        \n\t"
    "  popl %%ebx               \n"
      : "=a" (head)
      :  "m" (*stack),
         "a" (stack->head),
         "d" (stack->count)
      :  "ecx"
  );
```Heres the same code section but from a later version, with the ebx pushing and popping stuff that should cure that error... probably

I'm guessing there'll  be a lot more errors though, and the end result probably wouldn't be much use, theres been a lot of work since then. see previous warning!

---

### Post by searchfgold6789 on 2011-11-26
Cool, but what file do I put it in?
Thanks!

---

### Post by SevenMachines on 2011-11-26
In the source directory```
$ find ./ -name 'gsttrashstack.h'
./gst/gsttrashstack.h
```
The asm block you replace should start on line 103, as mentioned in the compiler error.

---

