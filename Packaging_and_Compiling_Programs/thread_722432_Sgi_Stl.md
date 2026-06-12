---
title: "Sgi Stl"
date: 2008-03-12
forum: Packaging and Compiling Programs
---

### Post by Rij on 2008-03-12
Hello,
Does Ubuntu have the SGI implementation of STL? I am trying to use hash_map in my programs but it will not compile. If not, how can I get it installed?
Also, how does one check for this?

---

### Post by KaeseEs on 2008-03-13
[quote=/usr/include/c++/4.1.3/vector] * Copyright (c) 1996
     * Silicon Graphics Computer Systems, Inc.
[/quote]

Ubuntu ships with g++ as its C++ compiler, which uses GNU libstdc++ as its STL implementation.  This implementation is heavily based on code from HP and SGI's STLs.  Because hash_map isn't standard, but an STL extension, it's included in the ext subdirectory of your main include path.  So, to use it, replace```
#include <hash_map>
```with```
#include <ext/hash_map>
```

Good luck!

---

