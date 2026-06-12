---
title: "Missing dbus-arch-deps.h"
date: 2007-03-20
forum: Programming Talk
---

### Post by mk1970 on 2007-03-20
Hi,

I'm trying dbus programming and even the simplest compilation test fails. What am I doing wrong? I can't locate this dbus-arch-deps.h anywhere...

```
%  dpkg -l | grep dbus | grep dev
ii  libdbus-1-dev                    1.0.2-1ubuntu3                         simple interprocess messaging system (develo

% cat test.c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <assert.h>

#include <dbus/dbus.h>

int
main (int argc, char **argv)
{

  return 0;
}

% gcc -Wall -I/usr/include/dbus-1.0 test.c
In file included from test.c:6:
/usr/include/dbus-1.0/dbus/dbus.h:29:33: error: dbus/dbus-arch-deps.h: No such file or directory
In file included from /usr/include/dbus-1.0/dbus/dbus-address.h:30,
                 from /usr/include/dbus-1.0/dbus/dbus.h:30,
                 from test.c:6:

```

---

### Post by mk1970 on 2007-03-20
The solutions seems to be pkgconfig, i.e. I was missing -I/usr/lib/dbus-1.0/include from the command line...

```
% pkg-config --cflags dbus-1
-I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  

% pkg-config --libs dbus-1
-ldbus-1  
```

---

