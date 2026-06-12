---
title: "gcc -Idir"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by ePascoal on 2011-10-21
Hi,

#include "mylib.h"

how can i link mylib address when im compiling my program.
i supose that is someting like this:  gcc -o file file.c -l/mydir/include/mylib/mylib,h

(l is a small L)
best regards,
ePascoal

;) Sorry if this subject doesn't fit in this forum.

---

### Post by gsmanners on 2011-10-21
Let's see...

```
gcc -o file file.c -l/mydir/include/mylib/mylib,h
```

Okay "-l" expects a library (a .o file or something like that).

For headers and such, you want "-I" (capital i), so something like this:

```
gcc -o file file.c -I/mydir/include/mylib
```

This is a subject for [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) ... might want to check out that forum.

---

