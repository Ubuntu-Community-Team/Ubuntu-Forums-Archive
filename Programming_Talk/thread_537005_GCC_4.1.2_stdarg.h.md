---
title: "GCC 4.1.2 stdarg.h"
date: 2007-08-28
forum: Programming Talk
---

### Post by nano2 on 2007-08-28
hi ,

looking at at problem here when compiling  a program using gcc4.1.2 on ubuntu
error: macro "va_start" requires 2 arguments, but only 1 given

I am using stdarg.h  using the following flags 

-Wno-deprecated -DHAVE_VPRINTF -DUSE_STDARGS -D__STDC__ -fno-access-control -fPIC -Wall -fpermissive

I get the following error message 
 error: expected declaration specifiers before âva_dclâ
 error: macro "va_start" requires 2 arguments, but only 1 given
error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â{â token

Any one know a work around or flag I am missing .
TIA

---

### Post by hod139 on 2007-08-28
My guess is that you are using the old posix varargs.h implementation.  See [http://en.wikipedia.org/wiki/Stdarg.h#.3Cvarargs.h.3E](http://en.wikipedia.org/wiki/Stdarg.h#.3Cvarargs.h.3E)

---

### Post by nano2 on 2007-08-29
I have compiled a sample program ..
and it looks like it is picking up the gcc4.1.2/stdarg.h# 1 "test.c"

# 1 "<built-in>"
# 1 "<command line>"
# 1 "test.c"
# 1 "/usr/lib/gcc/i486-linux-gnu/4.1.2/include/stdarg.h" 1 3 4
# 43 "/usr/lib/gcc/i486-linux-gnu/4.1.2/include/stdarg.h" 3 4
typedef __builtin_va_list __gnuc_va_list;
# 105 "/usr/lib/gcc/i486-linux-gnu/4.1.2/include/stdarg.h" 3 4
typedef __gnuc_va_list va_list;
# 2 "test.c" 2
int summate (int n, ...)
{
 va_list ap;
 int i = 0;


        VA_START(ap,n);
 for (; n; n--)
  i += __builtin_va_arg(ap,int);
  __builtin_va_end(ap);
  return i;

Also I have diverted the varargs.h to use stdargs.h

My varargs.h file has the following :

#ifdef __STDC__
#include <stdarg.h>
#else
#include <varargs.h>
#endif

Any other ideas as i have ran out work arounds myself .
TIA

---

### Post by hod139 on 2007-08-29
Maybe I was being unclear.  You gave no code in this post, all I had for information was:
> **nano2 said:**
> 
error: macro "va_start" requires 2 arguments, but only 1 given

The posix va_start took one argument, the standard va_start takes two.  The problem is not in including the wrong header, but in your usage of va_start.  This is why I referred you to the wikipedia article, so you can convert your usage from old style to new.  

va_start takes for parameters(int, va_list).  You seem to have it backwards in your code snippet.

---

