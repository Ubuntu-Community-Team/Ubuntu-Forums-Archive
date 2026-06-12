---
title: "How to handle includes in other directories with c++"
date: 2009-04-13
forum: Programming Talk
---

### Post by Neheb on 2009-04-13
I need help on how to handle folder structures when compiling c++ in ubuntu.

In the school project I am working on I got the app, include and src folders, app holding the file with main, and the two others for .h and .cpp files.

In visual studio I could just write #include "timer.h" in one of my cpp files and it would work, but how do I do the same thing in ubuntu? writing #include "../include/timer.h" (if it even works) just seems a bit stupid.

---

### Post by cabalas on 2009-04-13
You can either write ```
#include "../headers/timer.h"
``` or you can write just ```
#include "timer.h"
``` and when you compile pass the directory via the -I (uppercase i) option like so

```
g++ -c some_file.cc -I../include
```

That will tell the compiler to check the folder for headers that you are including.  Now my syntax may not be 100% right but if it isn't it should be close enough that you can figure out how to fix it.

---

### Post by Neheb on 2009-04-13
Thank you, that solved the problem.

---

