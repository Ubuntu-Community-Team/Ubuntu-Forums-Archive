---
title: "[SOLVED] gtk-tnutella failing to compile"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by echo314 on 2008-10-21
When I attempt to build the source code, I get the following error.
```
make[3]: Entering directory `/home/ed/Desktop/gtk-gnutella-snapshot/gtk-gnutella-snapshot/po'
rm -f de.gmo && msgfmt  -o de.gmo de.po
/bin/sh: msgfmt: not found
make[3]: *** [de.gmo] Error 127
make[3]: Leaving directory `/home/ed/Desktop/gtk-gnutella-snapshot/gtk-gnutella-snapshot/po'
make[2]: *** [stamp-po] Error 2
make[2]: Leaving directory `/home/ed/Desktop/gtk-gnutella-snapshot/gtk-gnutella-snapshot/po'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/ed/Desktop/gtk-gnutella-snapshot/gtk-gnutella-snapshot'
make: *** [all] Error 2

ERROR: Compiling failed.

```

---

