---
title: "Can't make deb-pkg linux kernel 3.18.30"
date: 2016-04-10
forum: Packaging and Compiling Programs
---

### Post by kr0n1x on 2016-04-10
Hi, I use vanilla kernels from kernel.org.
I've compiled the previous version of the kernel (3.18.29) successfully (I'm using it right now).

I tried patching it with the incremental patch (3.18.30), but I got the following errors:
```
  BUILDDEB
make[2]: warning: jobserver unavailable: using -j1.  Add '+' to parent make rule.
ln: target ‘./debian/tmp/lib/modules/3.18.30/source’ is not a directory
Makefile:1120: recipe for target '_modinst_' failed
make[2]: *** [_modinst_] Error 1
scripts/package/Makefile:90: recipe for target 'deb-pkg' failed
make[1]: *** [deb-pkg] Error 2
Makefile:1229: recipe for target 'deb-pkg' failed
make: *** [deb-pkg] Error 2
```

I thought it was my fault, some patching errors. So I downloaded the full linux kernel 3.18.30 and compiled it from scratch.

My commands (I copied my last working *.config* file):
```

make silentoldconfig
make -j3 deb-pkg
```

It failed again with the same errors. What could be the reason?

EDIT: My OS is Ubuntu Mate 15.10 64bit. Any more information needed?

---

