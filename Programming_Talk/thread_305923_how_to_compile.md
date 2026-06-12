---
title: "how to compile?"
date: 2006-11-24
forum: Programming Talk
---

### Post by robinoud on 2006-11-24
I create fist file to test ?
I begining  to learn C  language....
I write........

#include <stdio.h>
void main()
{
   printf("hello");
}

my source is right?
1. how to compile & run this source?
    I see help in program but I don't understand.
    Thank you.

---

### Post by engineer on 2006-11-24
to compile type

```
gcc -o programname filename.c
```

to run it, type

```
./programname
```

---

### Post by Arndt on 2006-11-24
> **robinoud said:**
> I create fist file to test ?
I begining  to learn C  language....
I write........

#include <stdio.h>
void main()
{
   printf("hello");
}


Don't trust anyone who tells you that "void main()" is portable.

---

