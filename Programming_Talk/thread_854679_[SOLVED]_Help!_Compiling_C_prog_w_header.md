---
title: "[SOLVED] Help! Compiling C prog w/ header"
date: 2008-07-09
forum: Programming Talk
---

### Post by picopir8 on 2008-07-09
It has been a while since I compiled anything on *nix so I am a bit of a newbie here.

Here is a simplified version of my program:
main.h
```

int main();
int foo(int x);

```

main.c
```

#include "main.h"

int main()
{
  ...
  foo(10);  // this is line number 50
  ...
}
int foo(int x) // this is line number 200
{
...
}

```

I compile using:
gcc -o main main.c

and get the following error:
main.c:200: error: conflicting types for 'foo'
main.c:50: error: previous implicit declaration of ‘foo’ was here

So if I include main.h, which has the prototype, for foo, then why does gcc think that line 50 is the declaration for foo?

I know I can put the declaration for foo above that of main to get this working, but what I dont understand is why the prototype in my header seems to be doing nothing.

---

### Post by skeeterbug on 2008-07-09
Is main.h in the same directory as main.c?

I just did:

$> touch main.h
$> touch main.c

Copied exactly what you have, did:

$> gcc -o main main.c
$>./main

It compiled and executed fine.

---

### Post by picopir8 on 2008-07-09
Thanks, your post prompted me to look in another direction and I found the problem.  It was not in the code that I posted.

This is a ported C++ program and main.h looked like this:
```
#if !defined(_MAIN_H)
#define _MAIN_H
...
#endif

```

The leading underscore on _MAIN_H was the killer.  I changed it to MAIN_H and it works great.

---

### Post by skeeterbug on 2008-07-09
> **picopir8 said:**
> Thanks, your post prompted me to look in another direction and I found the problem.  It was not in the code that I posted.

This is a ported C++ program and main.h looked like this:
```
#if !defined(_MAIN_H)
#define _MAIN_H
...
#endif

```

The leading underscore on _MAIN_H was the killer.  I changed it to MAIN_H and it works great.

Great, you can use #ifndef too.

---

