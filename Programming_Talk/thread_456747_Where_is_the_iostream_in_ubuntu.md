---
title: "Where is the iostream in ubuntu?"
date: 2007-05-28
forum: Programming Talk
---

### Post by yinglcs2 on 2007-05-28
I have 

#include <iostream> in my .c file, but when i compile it, I get this 
rtp.c:109:20: error: iostream: No such file or directory

can you please tell me what do i need to change my makefile to include and link in iostream file?

```
 gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I. -I../.. -DSYS_LINUX -I../../include -I/home/scheung/vlc-bin/include -D_FILE_OFFSET_BITS=64 -D__USE_UNIX98 -D_LARGEFILE64_SOURCE -D_REENTRANT -D_THREAD_SAFE -DLOCALEDIR=\"/home/scheung/vlc-bin/share/locale\" -DDATA_PATH=\"/home/scheung/vlc-bin/share/vlc\" -DPLUGIN_PATH=\"/home/scheung/vlc-bin/lib/vlc\" -O3 -ffast-math -funroll-loops -mtune=pentium2 -fomit-frame-pointer -D__LIBVLC__ -D__PLUGIN__ -DMODULE_NAME=stream_out_rtp -DMODULE_NAME_IS_stream_out_rtp -fvisibility=hidden -Wall -Wextra -Wno-unused-parameter -Wsign-compare -Wundef -Wpointer-arith -Wbad-function-cast -Wcast-align -Wwrite-strings -Wold-style-definition -Wmissing-prototypes -Wvolatile-register-var -MT libstream_out_rtp_plugin_la-rtp.lo -MD -MP -MF .deps/libstream_out_rtp_plugin_la-rtp.Tpo -c rtp.c  -fPIC -DPIC -o .libs/libstream_out_rtp_plugin_la-rtp.o
rtp.c:109:20: error: iostream: No such file or directory
rtp.c:114: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'namespace'
rtp.c:1486: warning: no previous prototype for 'socket_client'
rtp.c: In function 'socket_client':
rtp.c:1486: warning: old-style function definition
rtp.c:1494: error: 'cout' undeclared (first use in this function)
rtp.c:1494: error: (Each undeclared identifier is reported only once
rtp.c:1494: error: for each function it appears in.)
rtp.c:1495: error: 'cin' undeclared (first use in this function)
rtp.c:1517: error: 'cerr' undeclared (first use in this function)
rtp.c:1581: warning: 'return' with a value, in function returning void
```

---

### Post by Super_6_4 on 2007-05-28
In my install, all my c++ headers are in "/usr/include/c++/'version_number'/" - my version_number is 4.1.2. I'm pretty sure yours will at least be in /usr/include/. I'm not certain about anything past that. Hope it helps!

---

### Post by ankursethi on 2007-05-28
You seem to be compiling with gcc. C++ programs are compiled using g++.

---

