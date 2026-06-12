---
title: "C-scanf"
date: 2010-12-30
forum: Programming Talk
---

### Post by osbonkers on 2010-12-30
help me wid this.
scanf("%d%d"+scanf("%d%d",&i,&j));
printf("%d%d",i,j);...
What role '+'plays here..
on replacing it wid '-'..result varies.Why that?...

---

### Post by ziekfiguur on 2010-12-31
```
scanf("%d%d"+scanf("%d%d",&i,&j));
printf("%d%d",i,j);
```
This shouldn't compile, you are adding an integer to a char const *, that should not be possible without casting.
In the first scanf you also give to few arguments for the format, which should give a compile error as well.

---

### Post by MadCow108 on 2010-12-31
it compiles fine (at least with gcc), a string literal is represented as a pointer in C, and adding integers to pointers is legal.

scanf("%d%d", &i,&j); returns 2 (in case of success)
"%d%d" + 2 is equivalent to:
```

char a[] = "%d%d";
char * b = a + 2; // = "%d"

```
so the second scanf only expects a single integer instead of two

the problem is that the second scanf executed is missing an argument, so it writes the result into a random place in memory,
usually this results in a segmentation fault
Doing this should work (as long as the first scanf is successful!)
scanf("%d%d"+scanf("%d%d",&i,&j), &k);

but "%d%d" - 2 points to garbage memory and results in undefined behavior.
This also happens in the + case when scanf fails, which is why doing this is a bad idea.

---

### Post by ziekfiguur on 2010-12-31
> **MadCow108 said:**
> it compiles fine (at least with gcc), a string literal is represented as a pointer in C, and adding integers to pointers is legal.
What version of gcc are you using?

if i have this file:
```
#include <stdio.h>

int main()
{
    int i, j;
    scanf("%d%d"+scanf("%d%d",&i,&j));
    printf("%d%d",i,j);
    return 0;
}

```

and i try to compile it (with gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5), i get:
```
$ gcc test.c 
test.c: In function ‘main’:
test.c:6: warning: format not a string literal and no format arguments
```

You're right about adding integers to pointers though, my bad.

---

### Post by MadCow108 on 2010-12-31
its just a warning, it still compiles.
Of course it is a warning which must not be ignored in this case.
(The warning is a gcc extension, you can't rely on all compiler catching this, especially for pre C99 code)

The reason it is only a warning:
scanf("%d"+argc);
would give the same warning but is legal (gcc) code when argc is always 1 or 2

using this:
scanf("%d%d"+scanf("%d%d",&i,&j), &k);
gives you no warning (although in theory the compiler could detect the problem there to, but it doesn't).

---

