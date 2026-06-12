---
title: "error: stdio.h: No such file or directory"
date: 2011-06-22
forum: Programming Talk
---

### Post by tachyon4 on 2011-06-22
I recently installed Lucid on a new machine.  The command
```
gcc test.c
```yields the error "stdio.h: No such file or directory".  I get a similar error for each library I include.  The code works fine on my other machine, and I've checked that build-essential is installed.  The file /usr/include/stdio.h exists and looks normal.  What's going on?

---

### Post by schauerlich on 2011-06-22
Did you do

```
#include "stdio.h"
```

or

```
#include <stdio.h>
```

?

With quotes, it will look for stdio.h in the current directory. With angle brackets, it will look for it in the include path, which will have /usr/include in it.

---

### Post by tachyon4 on 2011-06-22
I use angle brackets.  Since I have no problem compiling the same code on my other machine, I doubt the problem is in the source.

---

### Post by Petrolea on 2011-06-23
If gcc can't find it means it isn't there. So maybe gcc is looking in a wrong directory.

---

### Post by slavik on 2011-06-23
try reinstalling build-essentials, also, output of `find /usr/include/ -name "stdio.h"` please.

EDIT: and you complete source code, copy/paste between code tags.

---

### Post by zobayer1 on 2011-06-23
Someone also posted a similar problem a few days ago, make sure you do not use spaces in between < >

---

### Post by montereybill on 2011-10-01
I found, in the man gcc page, that the gcc compiler needs an environment variable: GCC_INCLUDE_DIR

Putting this in .bashrc solved the problem:

GCC_INCLUDE_DIR=/usr/include/
export GCC_INCLUDE_DIR

If it's not in /usr/include do:

locate stdio.h

 and use that directory for GCC_INCLUDE_DIR.

Bill

---

