---
title: "C Programming"
date: 2009-12-02
forum: Programming Talk
---

### Post by lewisforlife on 2009-12-02
What is the difference between

```
#include "file.h"

```
and

```
#include <file.h>
```

---

### Post by Simian Man on 2009-12-02
The former searches the current directory for the file whereas the latter searches the system include path.  Use "" for files that you wrote that are part of the same project.  Use <> for files that are part of system libraries (these usually reside in /usr/include).

---

