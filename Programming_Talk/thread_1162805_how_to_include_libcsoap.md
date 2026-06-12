---
title: "how to include libcsoap?"
date: 2009-05-18
forum: Programming Talk
---

### Post by quintok on 2009-05-18
I'm getting a compiler error of missing library when I use:
#include <libcsoap/soap-server.h>

the .deb package installs soap-server.h to:
/usr/include/libcsoap-1.0/libcsoap/soap-server.h

but if I change it to:
#include <libcsoap-1.0/libcsoap/soap-server.h>
soap-server.h can't link to other headers (ie: soap-client.h) because it's referring to it as <libcsoap/soap-client.h>

newb question I'm sure =D
thanks you

---

### Post by quintok on 2009-05-18
CPPFLAGS, der.. tyvm anyway =)

for what it's worth using scons I did this:
env.Append(CPPPATH= ['/usr/include/libcsoap-1.0/', '/usr/include/nanohttp-1.0', '/usr/include/libxml2/'])

please note that it doesn't compile in C++ under jaunty, karmic has the bug fix required however.

---

