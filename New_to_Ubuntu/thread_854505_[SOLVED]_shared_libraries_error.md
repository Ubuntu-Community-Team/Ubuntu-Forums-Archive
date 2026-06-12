---
title: "[SOLVED] shared libraries error"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by mikeduffy13 on 2008-07-09
I have everything set up correctly to run vnc over ssh, but when I try to run the vncviewer -via command I always get this message.
```
vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```

I don't understand why this keeps happening.  I've tried 4 different ways to connect via vnc, and the only one I don't have problems with is vino (default remote desktop settings)...which I can't use because it doesn't allow for new sessions...argh!

---

### Post by mikeduffy13 on 2008-07-09
nm  - after a month of searching found the answer.

[www.rpmfind.net](www.rpmfind.net)

search for library, download rpm, install alien on unbuntu, run rpm install with alien, done.

---

### Post by nowshining on 2008-07-10
u could of also installed
```

libstdc++

&

libc6
```

from the repos.

---

