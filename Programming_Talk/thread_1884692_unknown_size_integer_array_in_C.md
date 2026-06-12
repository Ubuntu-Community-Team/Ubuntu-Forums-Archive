---
title: "unknown size integer array in C"
date: 2011-11-21
forum: Programming Talk
---

### Post by jacksonyoyo on 2011-11-21
Hi everyone, I'm new to this forum as well as C. 
At the moment, I want to create an unknown size integer array. 
As far as I know, this could be done using function malloc(), however, I do not know exactly as how should I do it

I googled it, and I found for char array:
```
int main(void)
{
char *array;

   array = malloc(sizeof("hello")); //<- Make your char pointer, point at the newly created space in memory.
   strcpy(array,"hello");           //<- Copy "hello" into the newly created array of chars.
   printf("%s",array);

   return 0;
}
```so, for integer array, can i just put:
```
array = malloc(sizeof(*int)); 
```Please help, thank you so much in advance. 
:popcorn:

============= THANK YOU SO MUCH FOR EVERYONE'S HELP! 
:lolflag:

---

### Post by gateway67 on 2011-11-21
An example:
```

#include <stdlib.h>

int main()
{
   const size_t NUM_VALS = 10;

   /* this allocates an array big enough to store NUM_VALS */
   int* array = malloc(NUM_VALS * sizeof(int));

   ...


   free(array);

   return 0;
}

```

---

### Post by San_SS! on 2011-11-21
In order to create arrays of unknown size at compile time you can use 3 functions:
 * malloc(size_t t): Reserves t bytes and returns a pointer to that area.
 * calloc(size_t num, size_t size): Reserves num sections of size bytes and initializes them to 0.
 * realloc(void *ptr, size_t size): You give it a pointer and it will resize it (if it can) to size bytes.

So if you want to create an array of ten ints and then resize it to 15 you would do something like:
```

int* array = malloc(10 * sizeof(int));
array = realloc(array, 15 * sizeof(int));

```

---

### Post by 3Miro on 2011-11-21
> **gateway67 said:**
> An example:
```

#include <stdlib.h>

int main()
{
   const size_t NUM_VALS = 10;

   /* this allocates an array big enough to store NUM_VALS */
   int* array = **(int*)** malloc(NUM_VALS * sizeof(int));

   ...


   free(array);

   return 0;
}

```

Technically this is the proper way of doing it. Depending on the compiler you may get a warning if you don't explicitly typecast.

malloc returns a generic void pointer (void*). int* is a pointer to an integer or array of integers (i.e. it points to one or more integers). malloc needs the size of the space that it must allocate and you need NUM_VALS times the size of one integer (i.e. NUM_VALS * sizeof(int) ).

---

### Post by Bachstelze on 2011-11-21
> **3Miro said:**
> Technically this is the proper way of doing it. Depending on the compiler you may get a warning if you don't explicitly typecast.

No. The standard explicitly allows conversions between a void pointer and another pointer type without an explicit cast.

> 6.5.4 Cast operators
Constraints
3 Conversions that involve pointers, other than where permitted by the constraints of 6.5.16.1, shall be specified by means of an explicit cast.


6.5.16.1 Simple assignment
Constraints
1 One of the following shall hold:
&#8212; the left operand has qualified or unqualified arithmetic type and the right has arithmetic type;
&#8212; the left operand has a qualified or unqualified version of a structure or union type compatible with the type of the right;
&#8212; both operands are pointers to qualified or unqualified versions of compatible types, and the type pointed to by the left has all the qualifiers of the type pointed to by the right;
**&#8212; one operand is a pointer to an object or incomplete type and the other is a pointer to a qualified or unqualified version of void, and the type pointed to by the left has all the qualifiers of the type pointed to by the right;**
&#8212; the left operand is a pointer and the right is a null pointer constant; or
&#8212; the left operand has type _Bool and the right is a pointer.

---

### Post by Dirich on 2011-11-22
Bach is right in saying that the standard does not require a cast. But 3Miro speaks the truth, as if you try ubuntu 11.10 and compile with gcc a code without the casts, than you get the warning (but I do not get a warning when the void assigned to the pointer is from the calloc):

I myself looked around about this matter not so long ago and I found a particularly nice form to use calloc (or malloc, ofc) is:

#define DIMENSION 5
int *o;

o = calloc(DIMENSION, sizeof(*o);

which makes you safe from any kind of type error, even if you were to change the type of your variables.

---

### Post by Arndt on 2011-11-22
> **Dirich said:**
> Bach is right in saying that the standard does not require a cast. But 3Miro speaks the truth, as if you try ubuntu 11.10 and compile with gcc a code without the casts, than you get the warning (but I do not get a warning when the void assigned to the pointer is from the calloc):

I myself looked around about this matter not so long ago and I found a particularly nice form to use calloc (or malloc, ofc) is:

#define DIMENSION 5
int *o;

o = calloc(DIMENSION, sizeof(*o);

which makes you safe from any kind of type error, even if you were to change the type of your variables.

When do you get the warning? Can you post a small example?

---

### Post by Dirich on 2011-11-22
> **Arndt said:**
> When do you get the warning? Can you post a small example?

Mmmhh... I get it when in my program (from the other thread: [http://ubuntuforums.org/showthread.php?t=1884351](http://ubuntuforums.org/showthread.php?t=1884351)) I modify line 44 in DRMgeneral.h, eliminating the cast to cpx.

Altough if I compile the following code no warning is issued...

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <complex.h>


typedef complex double cpx;

void * safeCalloc(size_t num, size_t size)
{
    void * ret;
    ret = calloc(num, size);
    if(ret == NULL)
    {
        printf("\nAllocation memory error!\n\n");
        exit(-1);
    }
    return ret;
}


int main()
{
    cpx *p;

    p = safeCalloc(2, sizeof(*p));

    free(p);

    return 0;
}

```When I compile my program instead I get the warning

warning: assignment makes pointer from integer without a cast [enabled by default]

---

### Post by Arndt on 2011-11-22
> **Dirich said:**
> Mmmhh... I get it when in my program (from the other thread: [http://ubuntuforums.org/showthread.php?t=1884351](http://ubuntuforums.org/showthread.php?t=1884351)) I modify line 44 in DRMgeneral.h, eliminating the cast to cpx.

Altough if I compile the following code no warning is issued...

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <complex.h>


typedef complex double cpx;

void * safeCalloc(size_t num, size_t size)
{
    void * ret;
    ret = calloc(num, size);
    if(ret == NULL)
    {
        printf("\nAllocation memory error!\n\n");
        exit(-1);
    }
    return ret;
}


int main()
{
    cpx *p;

    p = safeCalloc(2, sizeof(*p));

    free(p);

    return 0;
}

```When I compile my program instead I get the warning

warning: assignment makes pointer from integer without a cast [enabled by default]

Of course you get a warning if the compiler at that point doesn't know what safeCalloc returns. Only the code after safeCalloc in DRMsimulator.c knows that.

---

### Post by Dirich on 2011-11-22
> **Arndt said:**
> Of course you get a warning if the compiler at that point doesn't know what safeCalloc returns. Only the code after safeCalloc in DRMsimulator.c knows that.

But I have an header which defines safeCalloc, shouldn't it take care of that problem?
The tree of dependences is the following

DRMgeneral.h
           |
           |
------------------------------- 
|                 |            ...      |
aaa.h      bbb.h              zzz.h
|                 |            ...      |
aaa.c      bbb.c              zzz.c

Where by that I mean that xxx.c includes xxx.h and in xxx.h there's an include of DRMgeneral.h.
Should I include the header where I declare safeCalloc in DRMgeneral.h for everything in the program to know the definition of safeCalloc?

---

### Post by Arndt on 2011-11-22
> **Dirich said:**
> But I have an header which defines safeCalloc, shouldn't it take care of that problem?
The tree of dependences is the following

DRMgeneral.h
           |
           |
------------------------------- 
|                 |            ...      |
aaa.h      bbb.h              zzz.h
|                 |            ...      |
aaa.c      bbb.c              zzz.c

Where by that I mean that xxx.c includes xxx.h and in xxx.h there's an include of DRMgeneral.h.
Should I include the header where I declare safeCalloc in DRMgeneral.h for everything in the program to know the definition of safeCalloc?

You can structure the material any way you want, but if the declaration is present only in aaa.h and aaa.c, then the compilation of bbb.c won't see it.

One way is that DRMgeneral includes all the others, another way is that each C file which needs it includes aaa.h.

---

### Post by Dirich on 2011-11-23
> **Arndt said:**
> You can structure the material any way you want, but if the declaration is present only in aaa.h and aaa.c, then the compilation of bbb.c won't see it.

One way is that DRMgeneral includes all the others, another way is that each C file which needs it includes aaa.h.

I've tried both approaches when compiling with -Wall:

if I include in DRMgeneral.h every other .h what I get is a lot of errors because the compiler says pretty much everything defined in DRMgeneral.h is not defined and it can not recognize types and so in pretty much any .c file.

When I do something like this instead:
```


file1.h
#ifndef file1_h
#include "commonheader.h"
#include "file2.h"
<stuff>

int fff(); // function defined in file1.c which uses SSS(), a function declared in file2.h

<stuff>
#endif

---------------------------------------------------------------------------------------------------

file2.h
#ifndef file2_h
#include "commonheader.h"
#include "file1.h"
<stuff>

int SSS(int s)

 <stuff>
#endif

```The -Wall option gives me warning for both implicit declaration of function SSS in file1.c and an error for conflicting types for SSS in file2.h (when I got no error when compiling before adding the #include "file2.h" in file1.h and the addition of the -Wall).

I think there's some basic rule of how to pass the .c to the compiler that I am breaking? It seems the compiler sees SSS in file1.c first, decides on a certain definition and finds the real definition only later and that doesn't agree with what it thought. Either this or I have no idea :/

---

### Post by Bachstelze on 2011-11-23
Wrap something like this around DRMgeneral.h:

```
#ifndef DRMGENERAL_H_
#define DRMGENERAL_H_

/* Your other stuff...

#endif
```

That way you can include it as many times as you want, it will just not do anything after the first time.

---

### Post by gateway67 on 2011-11-23
> **Dirich said:**
> I've tried both approaches when compiling with -Wall:

if I include in DRMgeneral.h every other .h what I get is a lot of errors because the compiler says pretty much everything defined in DRMgeneral.h is not defined and it can not recognize types and so in pretty much any .c file.

When I do something like this instead:
```


file1.h
#ifndef file1_h
#include "commonheader.h"
#include "file2.h"
<stuff>

int fff(); // function defined in file1.c which uses SSS(), a function declared in file2.h

<stuff>
#endif

---------------------------------------------------------------------------------------------------

file2.h
#ifndef file2_h
#include "commonheader.h"
#include "file1.h"
<stuff>

int SSS(int s)

 <stuff>
#endif

```The -Wall option gives me warning for both implicit declaration of function SSS in file1.c and an error for conflicting types for SSS in file2.h (when I got no error when compiling before adding the #include "file2.h" in file1.h and the addition of the -Wall).

I think there's some basic rule of how to pass the .c to the compiler that I am breaking? It seems the compiler sees SSS in file1.c first, decides on a certain definition and finds the real definition only later and that doesn't agree with what it thought. Either this or I have no idea :/
Do not include a header file unless you require it.  In your example above, simply because you plan to call SSS() from within fff() does not imply that you need to include file2.h within file1.h.  However, you do need to include file2.h within file1.c, and of course within file2.c.

To elaborate using code...

File1.h:
```

#ifndef FILE1_H
#define FILE1_H

void fff();

#endif

```
File2.h:
```

#ifndef FILE2_H
#define FILE2_H

void sss();

#endif

```
File1.c:
```

#include "File1.h"   /* always include principal header file first */
#include "File2.h"   /* include dependent header file(s) next */

void fff()
{
   sss();
}

```
File2.c:
```

#include "File2.h"

void sss()
{
   /* blah */
}

```

---

