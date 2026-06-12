---
title: "GCC--compile with no default include path"
date: 2006-09-04
forum: Programming Talk
---

### Post by kinghajj on 2006-09-04
I'm trying to compile a small OS I wrote. I used to compile it with GCC 3.4 on Windows, but now I'm using GCC 4 and Ubuntu 6.06.

When I compile it, though, it gives me errors with redefining "size_t", "malloc", etc. It seems to be using the default includes (/usr/include/stdlib.h, etc.) when compiling, which is not good for compiling an OS. I need to know how to get GCC to stop including these files, as well as any file in the default include paths (/usr/include, /urs/local/include, etc.)

---

### Post by jpkotta on 2006-09-04
```
man gcc
```

>        
-nostdinc
           Do not search the standard system directories for header files.  Only the directories you have specified
           with -I options (and the directory of the current file, if appropriate) are searched.


---

