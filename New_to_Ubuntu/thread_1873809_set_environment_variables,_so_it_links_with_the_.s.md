---
title: "set environment variables, so it links with the .so files"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by Inebriated on 2011-11-01
> set environment variables, so it links with the .so files:
```

BASE=$HOME/Build
export PATH=$BASE/bin:$PATH
export LD_LIBRARY_PATH=$BASE/lib:$LD_LIBRARY_PATH
export PKG_CONFIG_PATH=$BASE/lib/pkgconfig:$PKG_CONFIG_PATH
export XDG_DATA_DIRS=$BASE/share:$XDG_DATA_DIRS

```

What does this mean?

---

### Post by LowSky on 2011-11-02
Could you tell us what you are trying to do? The code could be to anything without context.

---

