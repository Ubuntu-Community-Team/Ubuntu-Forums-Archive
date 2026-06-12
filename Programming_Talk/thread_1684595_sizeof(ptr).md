---
title: "sizeof(ptr)??"
date: 2011-02-09
forum: Programming Talk
---

### Post by Praveen30 on 2011-02-09
```

#include<stdio.h>
void main()
{
char *ptr;
printf("\n%d\n%d",sizeof(ptr),sizeof(*ptr));
}

```

output=2,1

1.i want to ask why the sizeof(ptr) is 2??
2.is this size compiler dependent??

---

### Post by MadCow108 on 2011-02-09
the size of pointers is machine/architecture dependent.
x86 has 4byte pointers, amd64 has 8 byte pointers
and your's seemingly has 2 byte pointers (or the compiler compiles code for a machine with 2byte pointers)

btw. the proper printf format for sizeof is %zu (in C99)

---

### Post by Simian Man on 2011-02-09
What machine and compiler are you on?  As MadCow said, the sizes are machine dependent, but machines with pointer sizes of two are...not common.

---

### Post by wmcbrine on 2011-02-09
Even the infamous Turbo C so beloved by our Indian friends shouldn't be giving a pointer size of 2, unless maybe it's set up to generate old-fashioned .COM files instead of .EXEs?

No, wait, it's starting to come back to me... [memory models](http://www.worldlingo.com/ma/enwiki/en/C_memory_model) called TINY, SMALL, LARGE and HUGE... with "near" and "far" pointers. Yeah, you could have two-byte pointers in several of those memory models.

---

### Post by Praveen30 on 2011-02-09
> **Simian Man said:**
> What machine and compiler are you on?  As MadCow said, the sizes are machine dependent, but machines with pointer sizes of two are...not common.

it is a turbo c 16bit compiler, on gcc it is giving 4.....depend on the architecture....

---

