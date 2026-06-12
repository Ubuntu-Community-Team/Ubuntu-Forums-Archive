---
title: "C Macro Inserting"
date: 2010-10-13
forum: Programming Talk
---

### Post by Mr.Macdonald on 2010-10-13
I want a macro

#define mac(x)

to do this

mac(add)

--Yields-->

__add__

---

### Post by GeneralZod on 2010-10-13
Do you mean something like this?

```

#include <stdio.h>

#define mac(x) __ ## x ## __

int main(void)
{
    int mac(x) = 3;
    printf("__x__ = %d", __x__);
    return 0;
}


```

Edit:

(See [here](http://gcc.gnu.org/onlinedocs/gcc-3.2.3/cpp/Concatenation.html#Concatenation) if you are curious).

---

### Post by nvteighen on 2010-10-14
> **GeneralZod said:**
> Do you mean something like this?

```

#include <stdio.h>

#define mac(x) __ ## x ## __

int main(void)
{
    int mac(x) = 3;
    printf("__x__ = %d", __x__);
    return 0;
}


```

Edit:

(See [here](http://gcc.gnu.org/onlinedocs/gcc-3.2.3/cpp/Concatenation.html#Concatenation) if you are curious).

Interesting... and this is even a standard preprocessor feature!

---

### Post by worksofcraft on 2010-10-14
> **nvteighen said:**
> Interesting... and this is even a standard preprocessor feature!
Yes... once again GeneralZod explains it so completely and so succinctly. He really does know C/C++ inside out I think!

---

### Post by GeneralZod on 2010-10-14
> **worksofcraft said:**
> Yes... once again GeneralZod explains it so completely and so succinctly. He really does know C/C++ inside out I think!

A long way away from this, alas :)

Oh, and I should probably point out: identifiers beginning with a double-underscore (like our __x__) are reserved for use by standard libraries and should generally be avoided, but I'm not sure if this applies only to C++ and not C.

---

