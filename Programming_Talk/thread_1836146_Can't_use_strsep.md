---
title: "Can't use strsep"
date: 2011-08-30
forum: Programming Talk
---

### Post by coweatyou on 2011-08-30
When I try to use strsep, I get a "implicit declaration of function ‘strsep’" warning.  I have included string.h and I have a man page for strsep but the compiler can't seem to find it.  Other functions from string.h work fine.

For reference, the line the compiler is complaining about is
```

char *nextword = strsep(&word, "\n");
```

---

### Post by Bachstelze on 2011-08-30
strsep is not standard. If you are using gcc, compile with -std=gnu99 instead of c99. However, it might be better to implement your own so you can be sure it will always be available.

---

### Post by johnl on 2011-08-30
```
   Feature Test Macro Requirements for glibc (see feature_test_macros(7)):

       strsep(): _BSD_SOURCE

....


CONFORMING TO
       4.4BSD.

```

Short answer: #define _BSD_SOURCE (or pass -D_BSD_SOURCE to gcc when compiling) to use **strsep**.

Long answer:  **strsep** is not a POSIX or Linux standard function, it's a BSD function.  This has portability implications if you are concerned about those sorts of things.  If you want your application to be portable you might want to use a different function.

---

### Post by coweatyou on 2011-08-30
> **Bachstelze said:**
> strsep is not standard. If you are using gcc, compile with -std=gnu99 instead of c99. However, it might be better to implement your own so you can be sure it will always be available.

That worked and I will implement my own but I want to get the stupid thing to work before I do.

---

