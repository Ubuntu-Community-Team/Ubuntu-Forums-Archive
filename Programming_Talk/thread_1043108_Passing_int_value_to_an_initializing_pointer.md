---
title: "Passing int value to an initializing pointer"
date: 2009-01-18
forum: Programming Talk
---

### Post by huangyingw on 2009-01-18
Hello, I always receive this kind of warning using GCC to compile,
How to solve it?
==========================================================
int main()
{
  const char *env =getenv ("MEMUSAGE_PROG_NAME");//this line could cause waring, how to solve it?
  return 0;
}


==========================================================

---

### Post by Zugzwang on 2009-01-18
C allows the usage of functions without prior declaration. In that case, "int" is assume to be the return value. To solve this problem, include a declaration of "getenv" that is found in "stdlib.h", so "include <stdlib.h>" before the main function and the warning disappears.

---

### Post by huangyingw on 2009-01-18
> **Zugzwang said:**
> C allows the usage of functions without prior declaration. In that case, "int" is assume to be the return value. To solve this problem, include a declaration of "getenv" that is found in "stdlib.h", so "include <stdlib.h>" before the main function and the warning disappears.
Great, that works for my case. Just hurry a thank to you first. I am busy at preparing returning home for the comming Spring Festival. I will try to delve into the description you mentioned later.

---

### Post by bruce89 on 2009-01-18
> **huangyingw said:**
> 
```
const char *env =getenv ("MEMUSAGE_PROG_NAME");
```

By the way, the definition of getenv is

```
char * getenv (const char *name)
```

---

### Post by huangyingw on 2009-01-19
> **bruce89 said:**
> By the way, the definition of getenv is

```
char * getenv (const char *name)
```
Also thank to you.

---

