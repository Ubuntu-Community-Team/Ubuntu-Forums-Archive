---
title: "asprintf()"
date: 2006-10-18
forum: Programming Talk
---

### Post by cronholio on 2006-10-18
What must I do to be able to use asprintf() in a C program (Dapper, gcc 4.0.3, glibc 1.2.10)? I included stdio.h, but I get an "implicit declaration" warning.

---

### Post by hod139 on 2006-10-18
From the [man page]("http://www.die.net/doc/linux/man/man3/asprintf.3.html"):
```

#define _GNU_SOURCE
#include <stdio.h>
...

```
Note, (also from the man page):  These functions are GNU extensions, not in C or POSIX. They are also available under *BSD. The FreeBSD implementation sets *strp* to NULL on error.

---

### Post by amo-ej1 on 2006-10-19
true, but in the first post he mentioned that stdio.h was already included.
On the other hand, the prototype actually _IS_ there:

```

e@lap:/usr/include$ cat stdio.h  | grep asprintf
extern int vasprintf (char **__restrict __ptr, __const char *__restrict __f,
extern int __asprintf (char **__restrict __ptr,
extern int asprintf (char **__restrict __ptr,

```

Are you really, really sure you included stdio ?

---

### Post by cronholio on 2006-10-19
> Are you really, really sure you included stdio ?

I am, I can even use sprintf(). I did not define _GNU_SOURCE, I changed that now but still it doesn't work.

---

### Post by po0f on 2006-10-19
cronholio,

How are you defining _GNU_SOURCE?  Usually, it's part of the compiler command, ie:
```
$ gcc -Wall -g -D_GNU_SOURCE -o mybinary mysource.c
```

Sometimes, define flags need to be set to a value, so if the above command doesn't work, try this:
```
$ gcc -Wall -g -D_GNU_SOURCE=1 -o mybinary mysource.c
```

---

### Post by hod139 on 2006-10-19
> **amo-ej1 said:**
> true, but in the first post he mentioned that stdio.h was already included.
Maybe my post was unclear.  You have to add the 
```

#define _GNU_SOURCE
```before including stdio.h.

On my machine:
```

#include <stdio.h>

int main()
{
  char *my_string;

  asprintf (&my_string, "Hello World.");
  puts (my_string);

  return 0;
}

```produces:
```

gcc -Wall temp.c
temp.c: In function ‘main’:
temp.c:8: warning: implicit declaration of function ‘asprintf’

```whereas:
```

#define _GNU_SOURCE 
#include <stdio.h>

int main()
{
  char *my_string;

  asprintf (&my_string, "Hello World.");
  puts (my_string);

  return 0;
}

```produces no warnings or errors.

Also, do you have the package build-essential installed?

---

