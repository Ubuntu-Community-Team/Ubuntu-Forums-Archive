---
title: "PLT Scheme compilation problem"
date: 2010-01-15
forum: Packaging and Compiling Programs
---

### Post by TPJ on 2010-01-15
I've been using Arch Linux for many years, and now I'm trying Kubuntu.

I need some Scheme implementations (PLT, Chicken, Gambit...). For start, I need PLT (DrScheme and others). Since PLT Scheme in Ubuntu repositories is rather outdated (4.1.5, while the current version is 4.2.3), I wanted to compile it and install from source. I managed to install development packages missing from the default Kubuntu installation, then I did configure, and then I tried to do make. Unfortunatelly, make returned the following error:

```
make[3]: Leaving directory `/home/tpj/opt/PLT/plt-4.1.5/src/build/mzscheme'
cd gc2; make all
make[3]: Entering directory `/home/tpj/opt/PLT/plt-4.1.5/src/build/mzscheme/gc2'
make xsrc/precomp.h
make[4]: Entering directory `/home/tpj/opt/PLT/plt-4.1.5/src/build/mzscheme/gc2'
env XFORM_PRECOMP=yes ../mzschemecgc -cqu ../../../mzscheme/gc2/xform.ss --setup . --cpp "gcc -E -DNEWGC_BTC_ACCOUNT  -I./.. -I../../../mzscheme/gc2/../include"  --keep-lines -o xsrc/precomp.h ../../../mzscheme/gc2/precomp.c
Segmentation fault
make[4]: *** [xsrc/precomp.h] Error 139
make[4]: Leaving directory `/home/tpj/opt/PLT/plt-4.1.5/src/build/mzscheme/gc2'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/tpj/opt/PLT/plt-4.1.5/src/build/mzscheme/gc2'
make[2]: *** [3m] Error 2
make[2]: Leaving directory `/home/tpj/opt/PLT/plt-4.1.5/src/build/mzscheme'
make[1]: *** [3m] Error 2
make[1]: Leaving directory `/home/tpj/opt/PLT/plt-4.1.5/src/build'
make: *** [all] Error 2
```

(I have translated the messages from Polish to English, where neccessary.)

I tried to compile a different versions (4.2 and 4.1.5), but the result was always the same.

Any idea on what can be wrong?

---

