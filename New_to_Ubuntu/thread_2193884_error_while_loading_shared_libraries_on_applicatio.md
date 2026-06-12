---
title: "error while loading shared libraries on application"
date: 2013-12-15
forum: New to Ubuntu
---

### Post by StevenHodges92 on 2013-12-15
I know this has been solved before but I can't figure out my specific problem with this application.  When I try to run it I get this

error while loading shared libraries: libboost_thread-gcc42-mt-1_34_1.so.1.34.1: cannot open shared object file: No such file or directory

---

### Post by DuckHook on 2013-12-15
> **StevenHodges92 said:**
> ...specific problem with this application...What's the application?

Knowing nothing else, you could try this, but be aware I'm throwing a Hail-Mary here:```
sudo apt-get install libboost-all-dev
```

---

### Post by steeldriver on 2013-12-15
it looks like the application may have been linked to a very specific (old) version of the library...?

---

