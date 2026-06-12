---
title: "Include header files in gcc/g++"
date: 2009-12-27
forum: Programming Talk
---

### Post by Binny88 on 2009-12-27
Hello guys

I want to know the options to include certain header files in gcc/g++ or to be more specific the path to these header files. The gcc manual is too extensive so I had to ignore it.

Thanks in advance
Binny

---

### Post by Bachstelze on 2009-12-27
```
cc -I/path/to/dir -o foo foo.c
```

---

### Post by falconindy on 2009-12-27
> **Binny88 said:**
> Hello guys

I want to know the options to include certain header files in gcc/g++ or to be more specific the path to these header files. The gcc manual is too extensive so I had to ignore it.

Thanks in advance
Binny
You can press '/' and search for terms in man pages.

Welcome to Linux. If something seems too difficult, there's probably an easier way to accomplish the task.

---

### Post by Bachstelze on 2009-12-27
> **falconindy said:**
> You can press '/' and search for terms in man pages.

Welcome to Linux. If something seems too difficult, there's probably an easier way to accomplish the task.

I'm not sure that would have helped much in this case...

---

### Post by monkeyking on 2009-12-28
> **Bachstelze said:**
> I'm not sure that would have helped much in this case...
I agree that the man pages can be quite incomprehensible :)
I wouldn't know what to search for in this case.

But a quick google would have solved you problem ;)

---

### Post by OVERPOWER8 on 2009-12-28
I think you need to place all the header files in the same folder where is the c file you are going to compile.

And to include header files, just write:

#include "Header.h"

or:
#include "full/path/to/header.h"

---

### Post by dwhitney67 on 2009-12-28
> **OVERPOWER8 said:**
> I think you need to place all the header files in the same folder where is the c file you are going to compile.

And to include header files, just write:

#include "Header.h"

or:
#include "full/path/to/header.h"
Wrong.  Please read Bachstelze's post.

---

