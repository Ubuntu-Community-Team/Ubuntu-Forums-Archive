---
title: "How to use Kdevelop, plz help"
date: 2008-03-29
forum: Programming Talk
---

### Post by smallvortex on 2008-03-29
Hi everybody, I have started learn to use KDE C++, when I try to call "syscalls.h", It shows that "there is no file or such directory", How can I include it to my program?

---

### Post by xelapond on 2008-03-29
Are you calling it with ```
#include "syscalls.h"
``` or ```
#include <syscalls.h>
```

The first one includes a header in the current project directory, and the second one includes it from the compilers path.

Hope that helps!

Alex

---

