---
title: "C &amp; getenv"
date: 2009-01-15
forum: Programming Talk
---

### Post by cl333r on 2009-01-15
Hi,
does anyone know why I get the warning "main.c:29: warning: initialization makes pointer from integer without a cast" for line
```

char *home = getenv("HOME");

```
and writing "char *home = (char *)getenv("HOME");" cancels the warning. The API states that a (char *) is being returned from getenv, why do I have to explicitly cast it?

---

### Post by dwhitney67 on 2009-01-15
Maybe because you forgot to include <stdlib.h>?

P.S.  You should also consider declaring your variable as a const char*.
```

const char* home = getenv("HOME");

```

---

### Post by cl333r on 2009-01-15
Thanks, that solved the issue.
The ability to reward the user seems to have been abolished.

---

