---
title: "[SOLVED] Injecting a shared library in a running Linux application"
date: 2008-11-29
forum: Programming Talk
---

### Post by WitchCraft on 2008-11-29
Hi, as you know you can inject a shared library in a Linux application with LD_PRELOAD.

However, this of course requires the application to be not yet started/started again.

On windows you can do dll injection to a running process with CreateRemoteProcess.

Since Linux has wine, I wondered whether I can use a Wine binary to inject a *.so with CreateRemoteProcess via wine in a native linux application...

Anybody knows whether this is possible?

---

### Post by jinksys on 2008-11-30
Linux also supports loading libraries on demand.  
I believe this can help you:

[http://www.ibm.com/developerworks/opensource/library/l-dll.html](http://www.ibm.com/developerworks/opensource/library/l-dll.html)

---

### Post by WitchCraft on 2008-12-09
Just found 2 injectors.

Doesn't work on amd64, though.

---

