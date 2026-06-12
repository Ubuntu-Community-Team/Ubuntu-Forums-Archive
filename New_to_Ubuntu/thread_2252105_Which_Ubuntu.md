---
title: "Which Ubuntu"
date: 2014-11-09
forum: New to Ubuntu
---

### Post by ray9 on 2014-11-09
I downloaded two versions of Ubuntu 14.04, one 32 bit and one 64 bit.  It seems as if I have the two DVD's mixed up.  How can I tell which is which?

---

### Post by ray9 on 2014-11-09
Ran both versions, both 32 bit.  I need more sleep.

---

### Post by claracc on 2014-11-09
You can run the following command in a xterm :

```
uname -a
```

If you obtain something as ```
Linux clara1 3.2.0-70-generic #105-Ubuntu SMP Wed Sep 24 19:49:46 UTC 2014 i686 i686 i386 GNU/Linux

```, the i386 says to you that it is a 32 bits release, but if you obtain something as:

```
Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```, the x86_64 part says to you that it is a 64 bits release.

---

