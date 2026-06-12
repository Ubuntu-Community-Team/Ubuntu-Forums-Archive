---
title: "Where is memcmp?"
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
 
 memcmp is OK but not memicmp. Where is it please?
 
PS I definitely mean memicmp (case independent). I tried _memicmp  :  same error

---

### Post by Tony Flury on 2012-03-22
memicmp I think it is only available on WIndows - and it is deprecated there too as far as i can find.

---

### Post by Bachstelze on 2012-03-22
The (POSIX) standard way to compare two strings in a case-insensitive way is strcasecmp().

---

