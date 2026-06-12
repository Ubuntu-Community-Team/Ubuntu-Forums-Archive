---
title: "[C++] error: No arguments to 'foo' that depend on a template parameter"
date: 2009-07-08
forum: Programming Talk
---

### Post by wbest on 2009-07-08
I'm porting Windows C++ code to Linux and am using g++
 
I keep getting errors along the lines of
 
error: there are no arguments to '_stricmp' that depend on a template parameter, so a declaration of '_stricmp' must be available
 
 
This comes from the line of code
 
return (-1U == len ? _stricmp(_Left, _Right) : _strnicmp(_Left, _Right, len));
 
I looked online for an explanation, but the only website I found was not very clear, and didn't seem to relate to my problem at all.
 
Any ideas?

---

### Post by lisati on 2009-07-08
> **wbest said:**
> I'm porting Windows C++ code to Linux and am using g++
 
I keep getting errors along the lines of
 
error: there are no arguments to '_stricmp' that depend on a template parameter, so a declaration of '_stricmp' must be available
 
 
This comes from the line of code
 
return (-1U == len ? _stricmp(_Left, _Right) : _strnicmp(_Left, _Right, len));
 
I looked online for an explanation, but the only website I found was not very clear, and didn't seem to relate to my problem at all.
 
Any ideas?
I don't have much C experience, and eve less C++ but here goes: I'm wondering if using strcmp instead of stricmp might make a difference.

---

### Post by MadCow108 on 2009-07-08
_stricmp is windows specific
strcasecmp should be the posix equivalent

---

### Post by JordyD on 2009-07-08
> **MadCow108 said:**
> _stricmp is windows specific
strcasecmp should be the posix equivalent
Uh-oh. He also says that he's getting a lot of them...

That's a lot of refactoring.

---

### Post by dwhitney67 on 2009-07-08
> **JordyD said:**
> Uh-oh. He also says that he's getting a lot of them...

That's a lot of refactoring.

It really depends on one's motivation.  If the person is smart, they could just develop their own _stricmp() family of functions.

```

#include <cstring>

int _stricmp(const char* lhs, const char* rhs)
{
  return strcasecmp(lhs, rhs);
}

int _strnicmp(const char* lhs, const char* rhs, size_t n)
{
  return strncasecmp(lhs, rhs, n);
}

```

---

### Post by smartbei on 2009-07-09
Or, you could write a quick script that would replace all of _stricmp with strcasecmp, etc. There are even some IDEs that can do this for you.

---

### Post by MadCow108 on 2009-07-09
```
#ifdef UNIX
#define _stricmp(x,y) strcasecmp(x,y)
#endif

```
should do it to
better because it may save extra function calls in performance critical sections

---

### Post by wbest on 2009-07-09
When I'm doing redfinitions of functions and procedures such as that above, can I just say f(x,y)?  Or do I have to actually say foo(char *c, int i)?

---

### Post by dwhitney67 on 2009-07-09
This should suffice:
```

#ifndef _MSC_VER
#define _stricmp(s1, s2)     strcasecmp(s1, s2)
#define _strnicmp(s1, s2, n) strncasecmp(s1, s2, (n))
#endif

```

---

### Post by wbest on 2009-07-09
> #define _strnicmp(s1, s2, n) strncasecmp(s1, s2, (n))
 
Why is the n in extra parenthesis in the Linux call?

---

### Post by dwhitney67 on 2009-07-09
I do not know if with today's compilers it is an issue or not, but yesteryear there used to be issues with passing a parameter that was derived from a mathematical expression.

For example:
```

#define AddTwo(n)   (n + 2)
...

int newNum = AddTwo(5 * 20);   // should yield 102

```
Before, such an operation may have yielded a value of 27, not the expected 102.

P.S.  It appears that today's compiler optimizes the arithmetic first, then calls the macro.

---

### Post by MadCow108 on 2009-07-09
> **wbest said:**
> When I'm doing redfinitions of functions and procedures such as that above, can I just say f(x,y)?  Or do I have to actually say foo(char *c, int i)?

what I posted is a so called macro
it just replaces certain elements of your code with the defined ones _before_ compilation, it does no type checking or whatever the compilation step does.
in the case I posted it just replaces the function _stricmp with 2 arguments with strcasecmp with the same arguments

you can do all kinds of stuff with macros, for example the C printf(format,...) statement is actually implemented as a macro (as C itsself does not allow arbitrary amounts of parameters)

but the use of macros can also lead to problems as for example the macro could replace stuff in your code you didn't want replaced.
Also extensive use of macros may be bad for the compiler optimization in certain cases.

---

### Post by dwhitney67 on 2009-07-09
> **MadCow108 said:**
> ...
you can do all kinds of stuff with macros, for example the C printf(format,...) statement is actually implemented as a macro (as C itsself does not allow arbitrary amounts of parameters)


Actually C does allow for an arbitrary amount of parameters; it is the reading of these arbitrary amount of parameters that relies on macros.  So technically, printf() is function, but it is the usage of va_start(), va_arg(), and va_end() in which the macros come into play.

---

### Post by MadCow108 on 2009-07-09
thanks for correcting, I actually meant that just said it in a wrong way :)
here's some info about it:
[http://docs.hp.com/en/B3901-90003/ch10s15.html](http://docs.hp.com/en/B3901-90003/ch10s15.html)

---

