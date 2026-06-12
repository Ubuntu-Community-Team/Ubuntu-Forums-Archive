---
title: "Constants within structures in C"
date: 2007-06-24
forum: Programming Talk
---

### Post by WebDrake on 2007-06-24
I would like to create a structure in C which always has, in any instance, a constant element of given value.

This should give an idea:
```

typedef struct {
    const char *name = "MyStruct";
    int var1;
    double var2;
} mystruct;

```

.... but that's not legal C code.  Is there a way to achieve what I want, so that I can ensure all variables of type mystruct have a constant element, .name, which is set equal to the string "MyStruct"?

Thanks in advance for any suggestions.

---

### Post by Mr. C. on 2007-06-24
A structure is only a template-like entity, which does not allocate space.  It merely helps compute reference offsets in the compiled code.

You need to create an instance of the structure by declaring a variable:

```
mystruct somevar;
```

This assigns an anonymous string to the name variable in the variable instance:
```
somevar.name = "MyStruct";
```

Create some preprocessor macros or initialization function that performs what you desire, so you can perform this in one step.

MrC

---

### Post by WebDrake on 2007-06-24
> **Mr. C. said:**
> Create some preprocessor macros or initialization function that performs what you desire, so you can perform this in one step.

That's a good suggestion.  I was hoping there was some way to ensure that *every possible instance of this structure contains this value* without any chance of it being otherwise.  I suppose I'm on a losing tack here?

---

### Post by WW on 2007-06-24
Something like this, maybe:

**mystruct.c**
```

#include <stdio.h>
#include <stdlib.h>

typedef struct {
    char *name;
    int var1;
    double var2;
} mystruct;


#define MyStruct_Declare(x)     mystruct x = {"MyStruct",0,0.0}
#define MyStruct_PtrDeclare(x)  mystruct * x

mystruct *MyStruct_Alloc()
{
    MyStruct_PtrDeclare(p);
    p = (mystruct *) malloc(sizeof(mystruct));
    p->name = "MyStruct";
    return p;
}

void MyStruct_Free(MyStruct_PtrDeclare(p))
{
    free(p);
}


int main()
{
    MyStruct_Declare(a);
    printf("a.name = \"%s\"\n",a.name);
    MyStruct_PtrDeclare(p);
    p = MyStruct_Alloc();
    printf("p->name = \"%s\"\n",p->name);
    MyStruct_Free(p);
    return 0;
}

```

```

$ gcc mystruct.c -o mystruct
$ ./mystruct
a.name = "MyStruct"
p->name = "MyStruct"
$

```
As long as you always use the MyStruct_Declare macro or the MyStruct_Alloc function to create the structures, it should work. (Creating an array of them is left as an exercise.)

Do you have a compelling reason to use C instead of C++?

---

### Post by j_g on 2007-06-25
No!

ALWAYS do error-checking on the return of malloc() to ensure that memory has indeed been allocated before you reference it. This is a very important issue. If you omit important error checking while you're writing code, then what happens is that, later as the source code builds up, it's typically a nightmare to go back and add that missing error-checking. Sometimes, it takes a major redesign to accomodate something that should have existed right from the beginning.

I really, really wish computer science books emphasized error checking. I've seen way too much code that omits it.

---

### Post by WebDrake on 2007-06-25
> **WW said:**
> Do you have a compelling reason to use C instead of C++?

Indeed, that's the question I'm asking myself.  Mainly it's that I'm much more comfortable and familiar with C than C++, but there's no time like the present to learn.

Thanks for the detailed explanation, with or without checking for successful memory allocation. ;-)

---

### Post by WW on 2007-06-25
> **j_g said:**
> No!

ALWAYS do error-checking on the return of malloc() to ensure that memory has indeed been allocated before you reference it.
This is a very good point.  I didn't mean to suggest that my code sample was the final implementation; it was meant to be enough to give the original poster some ideas for accomplishing his request.

---

