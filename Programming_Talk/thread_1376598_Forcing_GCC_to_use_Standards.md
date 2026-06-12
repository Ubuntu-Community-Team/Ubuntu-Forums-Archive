---
title: "Forcing GCC to use Standards"
date: 2010-01-09
forum: Programming Talk
---

### Post by Java Geek on 2010-01-09
Hello Everyone, 

I am beginning to learn pure C (Have been programming Java for several years) and I am running into a strange issue with the compiler (GCC). I intentionally wrote a program where all the variables were NOT declared at the beginning of a code block just to show my point.

```
#include <stdio.h>
int main()
{
    /* wrong!  The variable declaration must appear first */
    printf( "Declare x next" );

    int x = 0;
    printf("It does work: %d", x);

    return x;
}

```

That code shouldn't compile but it does. I even ran it like this and it still compiles:

```
stephen@Stephen-Desktop:~$ gcc -Wall -ansi -x c test.c
```

Does anybody know how I can force it to use standards?

---

### Post by Queue29 on 2010-01-09
You're looking for ```
-Werror
```

It will treat all warnings as errors, and fail to compile. Combined with -Wall, you'll be forced to follow very strict standards.

---

### Post by Java Geek on 2010-01-09
Wow, it STILL compiled! With no errors, warnings or anything!

---

### Post by wmcbrine on 2010-01-09
That *is* standard now, as of C99 (eleven years old, but only slowly being adopted). But if you want to make it conform to the most-widely used version of the C standard, C89:

```
gcc -std=c89 -pedantic *etc.*
```

The gcc man page says that "-ansi" is equivalent to "-std=c89", but also notes that "The -ansi option does not cause non-ISO programs to be rejected gratuitously. For that, -pedantic is required in addition to -ansi."

---

### Post by Java Geek on 2010-01-09
Oh my goodness! It worked! Thanks!!!

---

