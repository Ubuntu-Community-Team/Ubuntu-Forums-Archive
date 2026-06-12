---
title: "[SOLVED] How do I get the getenv() function to work?"
date: 2008-08-20
forum: Programming Talk
---

### Post by anewguy on 2008-08-20
I have written an application that needs to know a path, but I don't want to hard code the path.  So I set an environment variable to the path value and then tried getenv() in the C code.  When I try to compile it says that getenv() is being defined for the first time and then errors out.  I have tried including iostream, but it says iostream isn't found.  I installed another 1 of the glib dev libraries hoping that would fix it but to no avail.

So, can someone tell me what package I must need to install, and then what I need to include via #include in the program so that the following will copmile and work:

....
....
....
    char wrkpath[256];
....
....
....
    wrkpath = getenv("DAVEPATH");
....
....
....


I've omitted the portions of the code that already work and included only those related to the problem.

Thanks in advance!  :)

---

### Post by Joeb454 on 2008-08-20
Moved to programming talk :)

Also, make sure you have [build-essential]("apt://build-essential") installed (it's in the repo's :))

---

### Post by anewguy on 2008-08-20
Yep - already have build-essential.

---

### Post by scourge on 2008-08-20
[http://www.opengroup.org/onlinepubs/000095399/functions/getenv.html](http://www.opengroup.org/onlinepubs/000095399/functions/getenv.html)

You probably didn't include stdlib.h, or cstdlib if you're using c++.

Also, you should use "char *wrkpath" instead of "char wrkpath[256]".

---

### Post by dribeas on 2008-08-20
> **anewguy said:**
> 
```

    char wrkpath[256];
    wrkpath = getenv("DAVEPATH");

```


```

#include <stdlib.h>
...
   char* wrkpath;
   wrkpath = getenv( "DAVEPATH" );
   ...
   // Don't forget to free it at some later time
   free( wrkpath );

```

The function allocates the memory internally and then returns a pointer to the string (null terminated). Even if char[] and char* can be used similarly, an char[] cannot be assigned from a char* (the opposite is possible) or another char[], as it is a fixed pointer into a stack allocated memory chunk.

   David

---

### Post by dwhitney67 on 2008-08-20
> **dribeas said:**
> ```

#include <stdlib.h>
...
   char* wrkpath;
   wrkpath = getenv( "DAVEPATH" );
   ...
   // Don't forget to free it at some later time
   free( wrkpath );

```

The function allocates the memory internally and then returns a pointer to the string (null terminated). Even if char[] and char* can be used similarly, an char[] cannot be assigned from a char* (the opposite is possible) or another char[], as it is a fixed pointer into a stack allocated memory chunk.

   David
Dribeas (David), I have to disagree with you concerning the usage of free() in your code.  Placing that statement in the code leads a program to crash.  I'm using gcc 4.3.0 with Glibc 2.8.

Furthermore, the man-page for getenv() does not indicate that the caller must free any memory.

P.S.  Using 'valgrind' against a program that calls getenv() indicates that there are no memory leaks.

---

### Post by anewguy on 2008-08-20
> **dribeas said:**
> ```

#include <stdlib.h>
...
   char* wrkpath;
   wrkpath = getenv( "DAVEPATH" );
   ...
   // Don't forget to free it at some later time
   free( wrkpath );

```

The function allocates the memory internally and then returns a pointer to the string (null terminated). Even if char[] and char* can be used similarly, an char[] cannot be assigned from a char* (the opposite is possible) or another char[], as it is a fixed pointer into a stack allocated memory chunk.

   David

EXACTLY what I needed!!  Thanks!:)

---

### Post by jinksys on 2008-08-20
> **dwhitney67 said:**
> Dribeas (David), I have to disagree with you concerning the usage of free() in your code.  Placing that statement in the code leads a program to crash.  I'm using gcc 4.3.0 with Glibc 2.8.

Furthermore, the man-page for getenv() does not indicate that the caller must free any memory.

QFE.

@anewguy:
The getenv function does NOT allocate memory.  It simple searches an environment list provided by the host environment and returns a pointer to that area of memory.  If you try to free that range, which you do not own, bad things happen.  If you did not allocate it, don't free it.

---

### Post by IwarV on 2009-05-11
Complete agree about not freeing the memory for the returned char*.
My gripe is that this function should really return const char*.

Not sure what would happen, but as it stands the following example is valid:

```
[COLOR="DarkRed"]char[/COLOR]* var = ::getenv("HOME");

*var = '\n';
```

This construct would not be allowed by the compiler if the function forced the return type to const.

Obviously the work-around for the time being is to always cache the returned variable in a const char* yourself;

```
[COLOR="DarkRed"]const char[/COLOR]* var = ::getenv("HOME");

*var = '\n';   [COLOR="Green"]// compiler error![/COLOR]
```

---

