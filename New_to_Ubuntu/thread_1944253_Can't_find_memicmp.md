---
title: "Can't find memicmp"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by UncleRoy on 2012-03-20
// myfile.cpp

#include <string.h>

int ret = memicmp("ABC","Abc",3);

// ... etc

gives g++ error 
myfile.cpp:5:10: error: ‘memicmp’ was not declared in this scope

where is it please?

PS I tried _memicmp  :  same error

---

### Post by ksa618 on 2012-03-21
Do you mean memcmp? In that case, you just spelled it wrong.

---

### Post by UncleRoy on 2012-03-21
No. I really mean memicmp ( a case independent compare).
Is this deprecated or has it just disappeared if one uses ubuntu ?

---

