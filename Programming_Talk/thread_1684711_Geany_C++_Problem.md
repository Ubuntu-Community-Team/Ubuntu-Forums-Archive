---
title: "Geany C++ Problem?"
date: 2011-02-09
forum: Programming Talk
---

### Post by etdsbastar on 2011-02-09
Hello there,

I had just installed Geany for my C++ needs. I have created a new project and added two files main.cpp and main.h

Contents of main.cpp:
```
#include <stdio.h>
#include <main.h>

int main()
{
    printf(HEADERTXT);
}

```Contents of main.h:
```
const HEADERTXT "Hello World...";
```But, Geany is showing me the following error on compilation:

g++ -Wall -c "main.cpp" (in directory: /.../test-cpp)
main.cpp:2: fatal error: test-cpp/main.h: No such file or directory
compilation terminated.
Compilation failed.

**NOTE:** main.h is in the same folder as main.cpp

Anybody, please help and tell me how to add custom files and folders (complete project management)...

---

### Post by cgroza on 2011-02-09
The include line should be:

```
#include "main.h"
```

---

