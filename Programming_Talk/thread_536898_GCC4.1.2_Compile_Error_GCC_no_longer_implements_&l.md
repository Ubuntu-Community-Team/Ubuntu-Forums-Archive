---
title: "GCC4.1.2 Compile Error GCC no longer implements &lt;varargs.h&gt;."
date: 2007-08-28
forum: Programming Talk
---

### Post by nano2 on 2007-08-28
Hi ,

Having some difficulty in compiling a program 
that has the following 
#if defined (__STDC__) &&defined (HAVE_VPRINTF)
# include <stdarg.h>
#else
#include <varargss.h>
#endif

Now I want the Gcc to use stdarg.h
and i have the env set to do that 
AR="c++"
CC="gcc"
CPPFLAGS="-D__STDC__ -DHAVE_VPRINTF"
CXX="c++"
CXXFLAGS="-D__STDC__ -DHAVE_VPRINTF"

I am using gcc4.1.2 ubuntu 7.04 .
Anyone with any ideas how to overcome this error
LIBPATH=xxx ; unset LIBPATH ; \
        gcc -I../../../include -o ../../../bin/idlcpp cccp.c cexp.c 
In file included from cccp.c:184:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/varargs.h:4:2: error: #error "GCC no longer implements <varargs.h>."
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/varargs.h:5:2: error: #error "Revise your code to use <stdarg.h>."

Any ideas out there how i can force it to pick up stdarg.h 
Thanks in advance .

---

### Post by dwhitney67 on 2007-09-03
If I understand your post correctly, you want to implement a function/method that accepts a variable list of arguments.

If so, then here are snippets of code that can help you.

In the header file (.h):

```

class MyClass
{
  .
  .
  .
  void formatText( const char* format, ... );
};
```


In the implementation file (.cpp):

```
#include "MyClass.h>
#include <stdarg.h>
.
.
.
void
MyClass::formatText( const char* format, ... )
{
  char buf[ MAX_TEXT_SIZE ] = { 0 };

  va_list args;
  va_start( args, format );

  vsnprintf( buf, MAX_TEXT_SIZE, format, args );

  text = buf;
}
```

This is merely one example.  But I hope it helps.

---

### Post by fct on 2007-09-03
You are using CPPFLAGS and CXXFLAGS, that are flags for the C++ language. But you're compiling a C program. So I doubt the compiler is using those environment variables.

I suggest writing your own Makefile anyway. Will save you lots of typing.

---

### Post by public_void on 2007-09-03
If you don't want to use varargs.h then remove the #include directive for it. However if its across multiple source files, then are you sure that the macro definitions are being included as arguments for GCC.

---

