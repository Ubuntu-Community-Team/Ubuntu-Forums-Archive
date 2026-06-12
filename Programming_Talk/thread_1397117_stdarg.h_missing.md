---
title: "stdarg.h missing"
date: 2010-02-02
forum: Programming Talk
---

### Post by ABuNeNe on 2010-02-02
Hi guys, ain't stdarg.h a standard header file included in the c compiler? Problem is I can't find this file.```

/usr/include$ ls std*
stdint.h  stdio_ext.h  stdio.h    stdlib.h

```Any idea?

PS: The machine is running on Ubuntu 9.04 64bits

---

### Post by dwhitney67 on 2010-02-03
```

./c++/4.4/tr1/stdarg.h
./c++/4.3/tr1/stdarg.h

```

---

### Post by MadCow108 on 2010-02-03
your probably looking for the C header and not the C++ TR1 headers (which only include other headers on my system)

you can find these by checking the compilers include paths:
compile something with -v and look for this output:

#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.4.1/include
 /usr/lib/gcc/i486-linux-gnu/4.4.1/include-fixed
 /usr/include

my stdarg.h was found in /usr/lib/gcc/i486-linux-gnu/4.4.1/include
which is logical as it is implemented with gcc builtins and not using glibc

---

### Post by ABuNeNe on 2010-02-03
Any idea how do I include in my source file?

```

#include <stdarg.h>
...

```

---

### Post by denarced on 2010-02-04
> **ABuNeNe said:**
> Any idea how do I include in my source file?

```

#include <stdarg.h>
...

```

Check out what dwhitney67 said. Just leave out the first 2 characters. One or the other will work when compiling with g++.

---

### Post by dwhitney67 on 2010-02-04
Including stdarg.h in a program is not for the faint-hearted.  It requires skill and a good wrist.

This is what I had to do... First, in my editor of choice (vim), I typed the following:
```

#include <stdarg.h>

int main(void)
{
   return 0;
}

```
Then with determination, I typed the following at the terminal:
```

gcc test.c

```
For grins, and for extra credit, I saved the file with a .cpp extension, and recompiled it using g++ as such:
```

g++ test.cpp

```

Does this help you ABuNeNe?

P.S.  I tested the code on a RHEL 5.4 system.  And also on an Ubuntu 9.10 system.

---

