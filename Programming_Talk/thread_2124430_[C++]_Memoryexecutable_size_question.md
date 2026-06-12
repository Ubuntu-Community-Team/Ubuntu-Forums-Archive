---
title: "[C++] Memory/executable size question"
date: 2013-03-10
forum: Programming Talk
---

### Post by bird1500 on 2013-03-10
Hi,
I have a "enums.h" file with common utility enums and consts declared like:

```
enum ViewMode {
    VIEW_MODE_NONE = 0,
    VIEW_MODE_LIST = 1,
    VIEW_MODE_GRID = 2
};
```

Including it in a .cpp file makes the compilation unit larger (and hence the final executable and memory size) only **by the enums/consts actually used** in the .cpp file or **by all the enums/consts** defined in the "enums.h"?

---

### Post by sanguinoso on 2013-03-13
Generally speaking the compiler is smart enough to know that you didn't reference the variable anywhere in the .cpp and the memory usage of your application should not be any larger. The binary will slightly larger as that code will be in there.

---

### Post by MG&amp;TL on 2013-03-13
I could be wrong, but if I understand the C++ compile process correctly, the enum won't make any difference whatsoever unless you have debugging symbols set. The C preprocessor will just substitute instances of the enum to its appropriate value, e.g.:

```
int i = VIEW_MODE_NONE;
```

would become:

```
int i = 0;
```

---

### Post by trent.josephsen on 2013-03-13
I think enums are type-checked, so it's not done by the preprocessor. But you're right that it should make no difference whatsoever to the generated code. Enumeration constants are just that, constants -- they don't incur any overhead over an integer literal.

---

### Post by MG&amp;TL on 2013-03-13
> **trent.josephsen said:**
> I think enums are type-checked, so it's not done by the preprocessor. 

Huh. I thought it was just a neat way of #define 'ing multiple constants. Thanks for the hint!

---

### Post by MadCow108 on 2013-03-13
it is correct that enums are not preprocessed, they only represent integers which are (in x86 at least) directly representable in machine code, so no explicit load from memory is required and they should not increase the executable size by much (depending on the size of the number)

e.g.:
this:
```
enum {
    VAR = 431 
} my_enum;

int f(int a)
{
    if (a == VAR)
        return 1;
    return 0;
}

```
essentially results in this:
```
81 ff af 01 00 00    	cmp    $0x1af,%edi
```

---

