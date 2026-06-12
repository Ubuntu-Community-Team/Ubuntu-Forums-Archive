---
title: "error with mingw (gcc) and stdlib"
date: 2009-01-19
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-19
so im making a BF interpreter because my other projects needed boost and boost didnt like them :(

but i got to compile my code that includes stdlib.h and i get this error

```
In file included from inter.c:1:
C:/MinGW/bin/../lib/gcc/mingw32/3.4.5/../../../../include/stdlib.h:317: error: syntax error before "double"

--- errorlevel 1
```

heres the line in stdlib.h

[PHP]inline double __cdecl __MINGW_NOTHROW strtod (const char* __restrict__ __nptr, c[/PHP]

---

