---
title: "C building my own library"
date: 2012-02-12
forum: Programming Talk
---

### Post by ibrahimtawbe on 2012-02-12
i'm using 
```

libunp.a    :    unp.h
                gcc -Wall -Wstrict-prototypes -ansi -pedantic -g -c *.c -D_BSD_SOURCE;
                ar -cvq libunp.a *.o

```
should I clean .o files in the current directory after adding them to .a library

---

### Post by Arndt on 2012-02-12
> **ibrahimtawbe said:**
> i'm using 
```

libunp.a    :    unp.h
                gcc -Wall -Wstrict-prototypes -ansi -pedantic -g -c *.c -D_BSD_SOURCE;
                ar -cvq libunp.a *.o

```
should I clean .o files in the current directory after adding them to .a library

I can't come up with a situation where it matters.

---

