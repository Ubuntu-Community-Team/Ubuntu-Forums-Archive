---
title: "[SOLVED] Pulse Audio install issues"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by timstone on 2008-10-04
I've been trying to install this damned thing for about 20 minutes now and it's just driving me nuts, maybe someone with more experience can figure it out.

I extract, ./configure and make and when i do sudo make install i get this at the end

```

C -DPIC -o .libs/libpulse_la-pstream.o
cc1: warning: ../libltdl: No such file or directory
In file included from ./pulsecore/sink-input.h:34,
                 from ./pulsecore/core.h:41,
                 from ./pulsecore/core-scache.h:26,
                 from pulsecore/pstream.c:47:
./pulsecore/module.h:26:18: error: ltdl.h: No such file or directory
In file included from ./pulsecore/module.h:31,
                 from ./pulsecore/sink-input.h:34,
                 from ./pulsecore/core.h:41,
                 from ./pulsecore/core-scache.h:26,
                 from pulsecore/pstream.c:47:
./pulsecore/modinfo.h:37: error: expected ‘)’ before ‘dl’
In file included from ./pulsecore/sink-input.h:34,
                 from ./pulsecore/core.h:41,
                 from ./pulsecore/core-scache.h:26,
                 from pulsecore/pstream.c:47:
./pulsecore/module.h:38: error: expected specifier-qualifier-list before ‘lt_dlhandle’
make[3]: *** [libpulse_la-pstream.lo] Error 1
make[3]: Leaving directory `/home/tim/Desktop/pulseaudio-0.9.12/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tim/Desktop/pulseaudio-0.9.12/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tim/Desktop/pulseaudio-0.9.12'
make: *** [all] Error 2
tim@tim-desktop:~/Desktop/pulseaudio-0.9.12$ sudo make install
Making install in src
make[1]: Entering directory `/home/tim/Desktop/pulseaudio-0.9.12/src'
make  install-am
make[2]: Entering directory `/home/tim/Desktop/pulseaudio-0.9.12/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I..    -I../src -I../src/modules -I../src/modules/rtp -I../src/modules/gconf -pthread -D_POSIX_PTHREAD_SEMANTICS -I../libltdl   -I/usr/local/include   -DPA_DLSEARCHPATH=\"/usr/local/lib/pulse-0.9/modules/\" -DPA_DEFAULT_CONFIG_DIR=\"/usr/local/etc/pulse\" -DPA_BINARY=\"/usr/local/bin/pulseaudio\" -DPA_SYSTEM_RUNTIME_PATH=\"/usr/local/var/run/pulse\" -DPA_SYSTEM_CONFIG_PATH=\"/usr/local/var/lib/pulse\" -DPA_SYSTEM_STATE_PATH=\"/usr/local/var/lib/pulse\" -DAO_REQUIRE_CAS -DPULSE_LOCALEDIR=\"/usr/local/share/locale\" -DPA_MACHINE_ID=\"/usr/local/var/lib/dbus/machine-id\" '-DDEBUG_TRAP=__asm__("int $3")'   -g -O2 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math -MT libpulse_la-pstream.lo -MD -MP -MF .deps/libpulse_la-pstream.Tpo -c -o libpulse_la-pstream.lo `test -f 'pulsecore/pstream.c' || echo './'`pulsecore/pstream.c
 gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I.. -I../src -I../src/modules -I../src/modules/rtp -I../src/modules/gconf -pthread -D_POSIX_PTHREAD_SEMANTICS -I../libltdl -I/usr/local/include -DPA_DLSEARCHPATH=\"/usr/local/lib/pulse-0.9/modules/\" -DPA_DEFAULT_CONFIG_DIR=\"/usr/local/etc/pulse\" -DPA_BINARY=\"/usr/local/bin/pulseaudio\" -DPA_SYSTEM_RUNTIME_PATH=\"/usr/local/var/run/pulse\" -DPA_SYSTEM_CONFIG_PATH=\"/usr/local/var/lib/pulse\" -DPA_SYSTEM_STATE_PATH=\"/usr/local/var/lib/pulse\" -DAO_REQUIRE_CAS -DPULSE_LOCALEDIR=\"/usr/local/share/locale\" -DPA_MACHINE_ID=\"/usr/local/var/lib/dbus/machine-id\" "-DDEBUG_TRAP=__asm__(\"int \$3\")" -g -O2 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math -MT libpulse_la-pstream.lo -MD -MP -MF .deps/libpulse_la-pstream.Tpo -c pulsecore/pstream.c  -fPIC -DPIC -o .libs/libpulse_la-pstream.o
cc1: warning: ../libltdl: No such file or directory
In file included from ./pulsecore/sink-input.h:34,
                 from ./pulsecore/core.h:41,
                 from ./pulsecore/core-scache.h:26,
                 from pulsecore/pstream.c:47:
./pulsecore/module.h:26:18: error: ltdl.h: No such file or directory
In file included from ./pulsecore/module.h:31,
                 from ./pulsecore/sink-input.h:34,
                 from ./pulsecore/core.h:41,
                 from ./pulsecore/core-scache.h:26,
                 from pulsecore/pstream.c:47:
./pulsecore/modinfo.h:37: error: expected ‘)’ before ‘dl’
In file included from ./pulsecore/sink-input.h:34,
                 from ./pulsecore/core.h:41,
                 from ./pulsecore/core-scache.h:26,
                 from pulsecore/pstream.c:47:
./pulsecore/module.h:38: error: expected specifier-qualifier-list before ‘lt_dlhandle’
make[2]: *** [libpulse_la-pstream.lo] Error 1
make[2]: Leaving directory `/home/tim/Desktop/pulseaudio-0.9.12/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/tim/Desktop/pulseaudio-0.9.12/src'
make: *** [install-recursive] Error 1
tim@tim-desktop:~/Desktop/pulseaudio-0.9.12$
```

---

### Post by Nepherte on 2008-10-04
Why are you trying to install pulseaudio? It is already installed on Ubuntu 8.04?

---

### Post by howefield on 2008-10-04
> **Nepherte said:**
> Why are you trying to install pulseaudio? It is already installed on Ubuntu 8.04?
The version the OP is trying to get isn't installed on Ubuntu 8.04.

---

### Post by Perfect Storm on 2008-10-04
is libltdl3-dev installed?

---

### Post by Nepherte on 2008-10-04
> **howefield said:**
> The version the OP is trying to get isn't installed on Ubuntu 8.04.
Ok, but does he need the new version?

If it's a dependency problem, you could try:
```
sudo apt-get build-dep pulseaudio
```

---

### Post by timstone on 2008-10-04
I'm actually trying to get past ALSA.  I've read that ALSA doesn't support stereo recording and I'd like to try and get it working.

---

### Post by timstone on 2008-10-04
> **Artificial Intelligence said:**
> is libltdl3-dev installed?

It is now, I'll see what happens, but I read the requirements page and thought I had all the required packages installed.

---

### Post by timstone on 2008-10-04
got it installed, now to figure out how to get it working :)

---

