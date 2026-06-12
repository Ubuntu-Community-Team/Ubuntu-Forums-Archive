---
title: "iFolder compile errors"
date: 2007-05-12
forum: Packaging and Compiling Programs
---

### Post by DrBair on 2007-05-12
I've been attempting to compile and package Novell's iFolder. I believe I have all the dependencies and ./configure goes fine. 

Compiling I get this error:
```
/usr/bin/ld CSPObjectIterator.o CSPropertyIterator.o CSPStore.o CSPStoreObject.o FlaimWrapper.o -oFlaimWrapper.so -L "../../../external/flaim/lxx86/gcc3/release" -lflm -lstdc++ -lpthread -shared
/usr/bin/ld: cannot find -lstdc++
make[3]: *** [FlaimWrapper.so] Error 1
make[3]: Leaving directory `/home/ryan/ifolder_build/simias-1.2.5347.1/src/FlaimProvider/FlaimWrapper'

```

libstdc++6-4.1-dev is installed. 

/usr/lib/gcc/i486-linux-gnu/4.1.2/ shows up in libtool's sys_lib_search_path_spec, so it should be finding what it needs. I can get it to compile by symlinking /usr/lib/libstdc++.so.6 to /usr/lib/libstdc++.so, but that's not really a valid solution for packaging purposes. 

Any tips?

---

