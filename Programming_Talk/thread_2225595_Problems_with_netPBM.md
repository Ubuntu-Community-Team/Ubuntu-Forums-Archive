---
title: "Problems with netPBM"
date: 2014-05-22
forum: Programming Talk
---

### Post by male2 on 2014-05-22
[FONT=arial]I am on Ubuntu 13.10, working on a piece of c code and keep getting an include error that I can't pinpoint the reason for.


fatal error: pgm.h: No such file or directory
#include <pgm.h>


The file exists however in /usr/local/include/pgm-5.1/pgm/pgm.h
I compile with gcc -lm -lnetpbm -o project.x project.c


[/FONT]

---

### Post by slickymaster on 2014-05-22
Moved to the **Programming Talk** sub-forum.

---

### Post by spjackson on 2014-05-22
The location of pgm.h suggest that you have built libnetpbm from  source yourself. You will need to tell gcc where to find the header and (probably) the library. Also, I suggest specifying the libraries a different order.
```

gcc -I/usr/local/include/pgm-5.1/pgm -L/usr/local/lib -o project.x project.c -lnetpbm -lm

```
Note that this assumes the libnetpbm library is in /usr/local/lib. Change the -L path if it is elsewhere.

---

