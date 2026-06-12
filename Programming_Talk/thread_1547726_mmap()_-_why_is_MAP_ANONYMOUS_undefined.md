---
title: "mmap() - why is MAP_ANONYMOUS undefined?"
date: 2010-08-07
forum: Programming Talk
---

### Post by crampus on 2010-08-07
I have a little test program that includes:
...
#include <sys/mman.h>
...
data = mmap(NULL, 4096, PROT_WRITE, MAP_SHARED | MAP_ANONYMOUS, -1, 0);
...

I'm developing on 64-bit Ubuntu 10.4
Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) )

The compiler complains:  
...error: ‘MAP_ANONYMOUS’ undeclared (first use in this function)
 
While MAP_SHARED, for instance, is known from sys/mman.h. A bit of research
shows that sys/mman.h depends on ...include/bits/mman.h and __USE_MISC
to control the definition of MAP_ANONYMOUS vs. MAP_SHARED. I'm obviously 
missing something quite about controlling non file-based inter-process shared memory use...?

any help much appreciated
crampus

---

### Post by Arndt on 2010-08-07
> **crampus said:**
> I have a little test program that includes:
...
#include <sys/mman.h>
...
data = mmap(NULL, 4096, PROT_WRITE, MAP_SHARED | MAP_ANONYMOUS, -1, 0);
...

I'm developing on 64-bit Ubuntu 10.4
Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) )

The compiler complains:  
...error: ‘MAP_ANONYMOUS’ undeclared (first use in this function)
 
While MAP_SHARED, for instance, is known from sys/mman.h. A bit of research
shows that sys/mman.h depends on ...include/bits/mman.h and __USE_MISC
to control the definition of MAP_ANONYMOUS vs. MAP_SHARED. I'm obviously 
missing something quite about controlling non file-based inter-process shared memory use...?

any help much appreciated
crampus

This is not much help, but I get this to compile without problems:

```
#include <stdlib.h>
#include <sys/mman.h>

int main()
{
 mmap(NULL, 4096, PROT_WRITE, MAP_SHARED | MAP_ANONYMOUS, -1, 0);
}
```

Maybe you can use gcc -E to get a clue what is happening.

---

### Post by crampus on 2010-08-13
Thanks for pointing me in the right direction. Your stub compiles clean here too, but:

gcc -D_POSIX_SOURCE .... does not. Same problem: no MAP_ANONYMOUS.

(Further research on POSIX_SOURCE/MAP_ANONYMOUS is clerly indicated :)

crampus

---

### Post by MadCow108 on 2010-08-13
that define is not enabled by _POSIX_SOURCE because its not part of posix:
[http://www.kernel.org/doc/man-pages/online/pages/man2/mmap.2.html](http://www.kernel.org/doc/man-pages/online/pages/man2/mmap.2.html)
> 
Of the above flags, only MAP_FIXED is specified in POSIX.1-2001.  However,
       most systems also support MAP_ANONYMOUS (or its synonym MAP_ANON).

it is included in _BSD_SOURCE, _SVID_SOURCE and _GNU_SOURCE (which is all in glibc)

---

