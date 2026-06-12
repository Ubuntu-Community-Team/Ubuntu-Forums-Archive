---
title: "how to remove assert in C ?"
date: 2011-07-08
forum: Programming Talk
---

### Post by lucasart on 2011-07-08
Hello

I'm writing C code with some assert(...) from assert.h. When I want to compile a "release" version, the only way I've found to remove the assert is as follows
```

#define NDEBUG
#include <assert.h>

```

Just to clarify, it's plain C (not C++), that I I compile as follows:
```

gcc -O3 -o ./chess *.c

```

Any idea how to remove the assert, *without* modifying a single line of code ?

Thank you

---

### Post by MadCow108 on 2011-07-08
use the -D flag:
```
gcc -DNDEBUG -O3 -o ./chess *.c
```

---

### Post by lucasart on 2011-07-08
> **MadCow108 said:**
> use the -D flag:
```
gcc -DNDEBUG -O3 -o ./chess *.c
```

Thanks

Just to confirm: is it correct to say that -DXXX is equivalent to writing
```

#define XXX

```
on top of every single *.c file ?

---

### Post by JupiterV2 on 2011-07-08
> **lucasart said:**
> Thanks

Just to confirm: is it correct to say that -DXXX is equivalent to writing
```

#define XXX

```
on top of every single *.c file ?

Yes.

You may also want to add the following:

```
#ifdef NDEBUG
#  include <assert.h>
#else               /* debugging not enabled */
#  define assert(x) /* empty macro to prevent errors */
#endif
```

This makes all those assertions not generate warnings or errors when assert.h isn't included in your sources. You will need to put that boilerplate into every one of your source files by copy and pasting it there or creating a "debug.h" header and including it into all your sources.

---

### Post by nvteighen on 2011-07-08
> **JupiterV2 said:**
> Yes.

You may also want to add the following:

```
#ifdef NDEBUG
#  include <assert.h>
#else               /* debugging not enabled */
#  define assert(x) /* empty macro to prevent errors */
#endif
```

This makes all those assertions not generate warnings or errors when assert.h isn't included in your sources. You will need to put that boilerplate into every one of your source files by copy and pasting it there or creating a "debug.h" header and including it into all your sources.

Actually, that is the only true solution to the problem. Just preventing inclusion of assert.h won't prevent linking with the C Standard Library, which obviously has assert() in it.

---

### Post by Bachstelze on 2011-07-08
> **nvteighen said:**
> Actually, that is the only true solution to the problem. Just preventing inclusion of assert.h won't prevent linking with the C Standard Library, which obviously has assert() in it.

One could also enclose each call to assert() between #ifdef/#endif.  I can't say I like the solution, though.  This will effectively make the program silently fail when something goes wrong, which I don't really like because it gives the false impression that everything is fine.  From a security standpoint at the very least, it's a very bad thing.  I say you should leave it have people report the bug to you when they encounter one.

---

