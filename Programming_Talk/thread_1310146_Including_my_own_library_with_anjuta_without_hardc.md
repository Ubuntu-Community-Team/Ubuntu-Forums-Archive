---
title: "Including my own library with anjuta without hardcoding  include path"
date: 2009-11-01
forum: Programming Talk
---

### Post by hofsmo on 2009-11-01
I'm trying to develop an application which uses it's own shared library, after opening the anjuta project in anjuta and comparing it with mine I got it to work however I had to hardcode the includepath, like this:
```
#include "/home/myname/projectname/lib/lib.h"
```

Does anyone know how to make it compile without hardcoding the path?

Many thanks

---

### Post by januzi on 2009-11-01
```

#include "headers/header.h"

```In the makefile You can use I (capital i):
-I/path/to/the/header.h

+ maybe:
-L/path/to/the/library.so -l(lowercase L)name_of_the_library (without "lib" and ".so", eg. libfltk.so => -lfltk)

---

### Post by hofsmo on 2009-11-02
Thanks it worked, I added this line -I '$(top_builddir)/lib/' with the '', in the entry field for C compiler flags under advanced target proeprties.

---

