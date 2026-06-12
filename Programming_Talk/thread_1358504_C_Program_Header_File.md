---
title: "C Program Header File"
date: 2009-12-18
forum: Programming Talk
---

### Post by lewisforlife on 2009-12-18
I am trying to learn about header files.  Here is a simple program that multiplies 2 numbers together:

multiply.c
```
#include <stdio.h>
#include "header.h"

int main (int argc, char *argv[])
{
int x = 0;
int y = 0;

scanf ("%d", &x);
scanf ("%d", &y);

printf("%d\n", multiply (x, y);

return 0;
}
```

header.h
```

int multiply (int num1, int num2);

```

multiplyfunc.c
```
#include "header.h"

int multiply (int num1, int num2)
{
return num1 * num2;
}
```

I compile this code with:
```
gcc multiply.c multiplyfunc.c -o multiply
```

This works great, however, I am trying to realize the point of header files, because I got rid of #include "header.h" in multiply.c and multiplyfunc.c and the program still compiled and linked fine and I was able to run my program.  Should I just get rid of header.h since it works fine without it?  If so, in what case would I use a header file?

---

### Post by Physical Hook on 2009-12-18
Header files are supposed to give you a set of methods or classes, not their declarations. Basically, you don't need them unless you've a big class or a lot of functions which would look prettier if moved to another file.

---

### Post by johnl on 2009-12-18
Try the following, with and without the header file.  Also try compiling with **-Wall**

```

/* main.c */
/* #include "foo.h" */

int main(int argc, char* argv[])
{
   int z = foo(3, 4, 5); /* pass 3 arguments to foo and get an int back */
   return z;
}

```

```

/* foo.c */
/* this doesn't quite match how we used foo in main.c ... */
void foo(double x) 
{
    x = x + 3; 
}

```

```

/* foo.h */
#ifndef _FOO_H_
#define _FOO_H_
void foo(double x);
#endif

```


That should help demonstrate why function prototypes are important :)

---

### Post by lisati on 2009-12-18
> **Physical Hook said:**
> Header files are supposed to give you a set of methods or classes, not their declarations. Basically, you don't need them unless you've a big class or a lot of functions which would look prettier if moved to another file.

I beg to respectfully differ on this one. We're talking "C" here, not "C++". Without the declarations in header files, the C compiler would typically know absolutely NOTHING about standard library functions.

---

### Post by Physical Hook on 2009-12-18
> **lisati said:**
> I beg to respectfully differ on this one. We're talking "C" here, not "C++". Without the declarations in header files, the C compiler would typically know absolutely NOTHING about standard library functions.

So a header file should contain **only** function/variable prototypes ? :neutral:

---

### Post by lisati on 2009-12-18
> **Physical Hook said:**
> So a header file should contain **only** function/variable prototypes ? :neutral:

That's *one* of the uses.

---

### Post by LKjell on 2009-12-18
> **Physical Hook said:**
> So a header file should contain **only** function/variable prototypes ? :neutral:

Actually you can add whatever you like in there. Just think of it as an aid to make code easier to read.

---

### Post by Arndt on 2009-12-18
> **LKjell said:**
> Actually you can add whatever you like in there. Just think of it as an aid to make code easier to read.

But don't put code there. Prototypes and preprocessor symbols and macros go there.

---

### Post by lewisforlife on 2009-12-18
> **Arndt said:**
> But don't put code there. Prototypes and preprocessor symbols and macros go there.

Do includes go in there?  Should I add include that are in multiple of my .c files in the header file.  For instance, if I need stdio.h in all of my .c files, can I just includes my header in all of them, and include stdio.h in my header?

---

### Post by Some Penguin on 2009-12-18
Traditionally, the header file shouldn't refer to any #includes that aren't necessary for the same component for which the header is providing prototypes.  That's so that if you separate this component for use in a library, the corresponding header doesn't pull in unnecessary things.

That said, you could do something like write a 'common.h' header or whatever that contains project-wide #includes and so forth, where you know you aren't intending for it to be #included by anything else.

---

### Post by lewisforlife on 2009-12-18
Thanks for all of your responses.  I think I have a better grasp on what header files are used for now.  Thread Solved!

---

