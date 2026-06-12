---
title: "Missing pthread.h"
date: 2009-03-09
forum: Packaging and Compiling Programs
---

### Post by dodle on 2009-03-09
When I use ./configure, it complains that pthread.h is missing.  What package is this in.  I can't seem to find it anywhere.  I have libpthread-stubs0 and libpthread-stubs0-dev installed.

```
....
checking for GGZ configuration tool: ggz-config... /usr/local/bin/ggz-config
checking for GGZ library: libggz... (cached) yes (libraries /usr/local/lib, headers /usr/local/include)
checking for GGZ library version: 0.0.14... yes
checking for GGZ library: ggzdmod... yes (libraries /usr/lib, headers /usr/include)
checking for GGZ server: ggzd... yes (/etc/ggzd)
checking pthread.h usability... no
checking pthread.h presence... no
checking for pthread.h... no
configure: error: *** Cannot find pthread.h header

```

**Edit:** I also have libpth20 and libpth-dev installed.

**Edit:** I have verified that /usr/include/pthread.h *does* exist, but ./configure can't seem to find it.

---

### Post by dodle on 2009-03-09
*deleted*

I figured out that my problems had nothing to do with pthread.h, but upgrading libglib.

---

