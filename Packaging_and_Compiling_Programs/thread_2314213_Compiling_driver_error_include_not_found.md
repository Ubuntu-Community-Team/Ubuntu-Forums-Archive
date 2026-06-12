---
title: "Compiling driver error: include not found"
date: 2016-02-19
forum: Packaging and Compiling Programs
---

### Post by pimdegreef on 2016-02-19
I get the following while compiling a driver for a PCI networkadapter:

```
from r8169.c:52:
/usr/src/linux-headers-3.13.0-63-generic/include/linux/linkage.h:7:25: fatal error: asm/linkage.h: Bestand of map bestaat niet
 #include <asm/linkage.h>
                         ^
compilation terminated.
make: *** [r8169.o] Fout 1
```

'Bestand of map bestaat niet' is Dutch for 'file or folder doesn't exist. I've googled it, and it seems to be a common problem. But I can't find any solution.

---

### Post by blueridgedog on 2016-02-21
Have you installed the source for your current kernel?  You can do so with the software tool.

---

