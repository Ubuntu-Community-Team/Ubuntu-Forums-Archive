---
title: "Can't find memicmp"
date: 2012-03-22
forum: Programming Talk
---

### Post by UncleRoy on 2012-03-22
// myfile.cpp

#include <string.h>

int ret1 = memcmp("ABC","Abc",3);
int ret2 = memicmp("ABC","Abc",3);
 
 // ... etc
gives g++ error myfile.cpp:7:11: error: ‘memicmp’ was not declared in this scope

where is it please?

PS I definitely mean memicmp (case independent). I tried _memicmp  :  same error

---

### Post by nothingspecial on 2012-03-23
Duplicate thread.

Closed.

---

