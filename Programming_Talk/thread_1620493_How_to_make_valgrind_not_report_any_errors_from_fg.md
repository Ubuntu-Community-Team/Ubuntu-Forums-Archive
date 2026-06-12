---
title: "How to make valgrind not report any errors from fglrx_dri.so?"
date: 2010-11-13
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-11-13
Edit: Problem solved :guitar:

ATI Catalyst drivers got bugs. And when I debug code which uses OpenGL, valgrind reports lots of errors from the graphics drivers:
```

==2887== Invalid write of size 1
==2887==    at 0x4C28E67: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6AF: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cffe is not stack'd, malloc'd or (recently) free'd
==2887== 
==2887== Invalid write of size 1
==2887==    at 0x4C28E72: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6AF: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cffd is not stack'd, malloc'd or (recently) free'd
==2887== 
==2887== Invalid write of size 1
==2887==    at 0x4C28E7D: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6AF: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cffc is not stack'd, malloc'd or (recently) free'd
==2887== 
==2887== Invalid write of size 1
==2887==    at 0x4C28E5D: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6C4: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cfff is not stack'd, malloc'd or (recently) free'd
==2887== 
==2887== Invalid write of size 1
==2887==    at 0x4C28E67: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6C4: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cffe is not stack'd, malloc'd or (recently) free'd
==2887== 

```

How can I suppress those errors? They fill the entire console and it makes finding the real errors that originate from my program very difficult.

Another example. Here's a self-compiling hello world program, hello.c:
```

#if 0
#!/bin/bash
gcc hello.c -std=gnu99 -Wall -lGL -o hello
exit
#endif

#include <stdio.h>
#include <GL/gl.h>

int main( int argc, char *argv[] )
{
  printf( "Hello World!\n" );
  return 0;
}

```
When I run it in valgrind --leak-check=full, I get:
```

==2991== 8 bytes in 1 blocks are definitely lost in loss record 1 of 3
==2991==    at 0x4C274A8: malloc (vg_replace_malloc.c:236)
==2991==    by 0x4E8D3EC: ??? (in /usr/lib/libGL.so.1.2)
==2991==    by 0x4E5C862: ??? (in /usr/lib/libGL.so.1.2)
==2991== 
==2991== 16 bytes in 1 blocks are definitely lost in loss record 2 of 3
==2991==    at 0x4C274A8: malloc (vg_replace_malloc.c:236)
==2991==    by 0x4E8D36D: ??? (in /usr/lib/libGL.so.1.2)
==2991==    by 0x4E5C862: ??? (in /usr/lib/libGL.so.1.2)
==2991== 
==2991== 24 bytes in 1 blocks are definitely lost in loss record 3 of 3
==2991==    at 0x4C274A8: malloc (vg_replace_malloc.c:236)
==2991==    by 0x4E8D2D9: ??? (in /usr/lib/libGL.so.1.2)
==2991==    by 0x4E5C862: ??? (in /usr/lib/libGL.so.1.2)

```

So how to make valgrind not report errors from libGL and fglrx_dri.so?

---

### Post by Arndt on 2010-11-13
> **crazyfuturamanoob said:**
> ATI Catalyst drivers got bugs. And when I debug code which uses OpenGL, valgrind reports lots of errors from the graphics drivers:
```

==2887== Invalid write of size 1
==2887==    at 0x4C28E67: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6AF: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cffe is not stack'd, malloc'd or (recently) free'd
==2887== 
==2887== Invalid write of size 1
==2887==    at 0x4C28E72: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6AF: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cffd is not stack'd, malloc'd or (recently) free'd
==2887== 
==2887== Invalid write of size 1
==2887==    at 0x4C28E7D: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6AF: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cffc is not stack'd, malloc'd or (recently) free'd
==2887== 
==2887== Invalid write of size 1
==2887==    at 0x4C28E5D: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6C4: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cfff is not stack'd, malloc'd or (recently) free'd
==2887== 
==2887== Invalid write of size 1
==2887==    at 0x4C28E67: memcpy (mc_replace_strmem.c:497)
==2887==    by 0xB83A6C4: ??? (in /usr/lib/dri/fglrx_dri.so)
==2887==  Address 0x7ff05590cffe is not stack'd, malloc'd or (recently) free'd
==2887== 

```

How can I suppress those errors? They fill the entire console and it makes finding the real errors that originate from my program very difficult.

Another example. Here's a self-compiling hello world program, hello.c:
```

#if 0
#!/bin/bash
gcc hello.c -std=gnu99 -Wall -lGL -o hello
exit
#endif

#include <stdio.h>
#include <GL/gl.h>

int main( int argc, char *argv[] )
{
  printf( "Hello World!\n" );
  return 0;
}

```
When I run it in valgrind --leak-check=full, I get:
```

==2991== 8 bytes in 1 blocks are definitely lost in loss record 1 of 3
==2991==    at 0x4C274A8: malloc (vg_replace_malloc.c:236)
==2991==    by 0x4E8D3EC: ??? (in /usr/lib/libGL.so.1.2)
==2991==    by 0x4E5C862: ??? (in /usr/lib/libGL.so.1.2)
==2991== 
==2991== 16 bytes in 1 blocks are definitely lost in loss record 2 of 3
==2991==    at 0x4C274A8: malloc (vg_replace_malloc.c:236)
==2991==    by 0x4E8D36D: ??? (in /usr/lib/libGL.so.1.2)
==2991==    by 0x4E5C862: ??? (in /usr/lib/libGL.so.1.2)
==2991== 
==2991== 24 bytes in 1 blocks are definitely lost in loss record 3 of 3
==2991==    at 0x4C274A8: malloc (vg_replace_malloc.c:236)
==2991==    by 0x4E8D2D9: ??? (in /usr/lib/libGL.so.1.2)
==2991==    by 0x4E5C862: ??? (in /usr/lib/libGL.so.1.2)

```

So how to make valgrind not report errors from libGL and fglrx_dri.so?

Did you read the manual page? There are so-called suppression files.

---

