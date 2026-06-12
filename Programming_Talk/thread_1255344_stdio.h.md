---
title: "stdio.h"
date: 2009-09-01
forum: Programming Talk
---

### Post by nebu on 2009-09-01
I want to see the implementation of the io library(stdio.h)....

when i go to /usr/include..... i just see the prototypes of the functions available there..... where is the actual body of the function defined??

from what i have understood.... these libraries are provided in their compiled forms anlong with the gcc compiler on the repository..... 

where do i get the source code for this file??

---

### Post by dwhitney67 on 2009-09-01
Go here:  [http://www.gnu.org/software/libc/](http://www.gnu.org/software/libc/)

Reference the links in the "Availability" section of the document.

---

### Post by nebu on 2009-09-01
thnx....


one more thing....

i am a little confused about this code....> 
unsigned int __pushed_back:1;

what exactly is the ":1" doing??

---

### Post by Arndt on 2009-09-01
> **nebu said:**
> thnx....


one more thing....

i am a little confused about this code....

what exactly is the ":1" doing??

Bit field, I suppose. Is it inside a struct?

---

### Post by nebu on 2009-09-01
ya

---

### Post by MadCow108 on 2009-09-01
that allows to pack bitfields into structs
```

struct pack {
 int one:8;
 int two:8;
};

```
this packs two 8 bit values into the struct
you can know access them easily with:
pack.one = 7

very useful if your reading something where many values are packed into a single larger type like an int as you can jsut cast that type to a appropriate struct and have easy access to the single values.

---

### Post by soltanis on 2009-09-01
In general:

```

struct example {
        unsigned int field : 3;
}

```

Field is specified to be an unsigned int, but the : 3 means it has a width of 3 bits. The width of the field cannot exceed the normal size of the variable type, and the way the structure is aligned in memory is implementation dependent. The unsigned declaration is important to keep the first bit in the field from being interpreted as a sign bit.

---

