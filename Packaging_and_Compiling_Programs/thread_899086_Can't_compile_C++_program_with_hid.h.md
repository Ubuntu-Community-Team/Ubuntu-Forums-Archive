---
title: "Can't compile C++ program with hid.h"
date: 2008-08-24
forum: Packaging and Compiling Programs
---

### Post by raccoonone on 2008-08-24
I'm having a problem using the headers from libhid, specifically hid.h. If I use it in a .c file it compiles fine, but if I rename the file to .cpp I get a bunch of errors. This is the testcase I made:
```

#include <hid.h>

int main()
{
	HIDInterfaceMatcher broken;
	return 0;
}
```
Naming the file "brokenhid.c" and compiling using "gcc brokenhid.c" works fine, but "g++ brokenhid.c" gives the following errors:
```

In file included from brokenhid.c:1:
/usr/include/hid.h:72: error: typedef ‘_Bool’ is initialized (use __typeof__ instead)
/usr/include/hid.h:72: error: ‘matcher_fn_t’ was not declared in this scope
/usr/include/hid.h:79: error: ‘matcher_fn_t’ does not name a type
/usr/include/hid.h:124: error: ‘_Bool’ does not name a type
/usr/include/hid.h:133: error: ‘_Bool’ does not name a type

```
Naming the file "brokenhid.cpp" and compiling with either gcc or g++ causes the same errors. My first thought was to wrap the #include in 'extern "C"', but that had no effect.
Anyone know what's wrong? I'm new to programming for Linux (recently migrated from Windows)

---

### Post by raccoonone on 2008-08-24
Solution is to include stdbool.h when compiling .cpp files

---

