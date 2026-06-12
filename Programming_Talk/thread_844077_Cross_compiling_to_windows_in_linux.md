---
title: "Cross compiling to windows in linux"
date: 2008-06-29
forum: Programming Talk
---

### Post by rraj.be on 2008-06-29
I have a c-program.

How can i make cross compilation to produce a .exe file so that i can run it in window's.

---

### Post by LaRoza on 2008-06-29
```

~$sudo aptitude install mingw32
~$cat p.c
#include <stdio.h>
int main(int argc, char ** argv)
{
    printf("Hello world\n");
} 
~$i586-mingw32msvc-gcc p.c
~$wine a.exe
Hello world
~$

```

---

