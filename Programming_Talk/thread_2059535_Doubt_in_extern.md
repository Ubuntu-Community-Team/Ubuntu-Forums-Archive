---
title: "Doubt in extern"
date: 2012-09-18
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-18
Hey,
I have a doubt in extern. I do know that
```

extern int a; //THIS IS DECLARATION

```

```

int a; //THIS IS DEFINITION

```


```

extern int a = 0; //THIS IS ALLOWED AND TAKEN AS DEFINITION

```

But I find this difficult to understand. Does it also depend on where it is defined ? 
```

#include <stdio.h>

extern int var = 0; // WORKS WHEN DECLARED/DEFINED HERE BUT GIVES A WARNING

int main(void)
{
// extern int var = 0; //DOESN'T WORK WHEN DECLARED/DEFINED HERE
 var = 10;

 printf("\nThis works correctly ");

 return 0;
}

```

---

### Post by dwhitney67 on 2012-09-18
A variable has to be declared somewhere; only after it has been declared can you declare it elsewhere using 'extern'.

In previous projects I've supported, I wrote header files with something like this:
```

#ifndef MY_HEADER_H
#define MY_HEADER_H

#ifdef MAIN
    #define EXTERN
#else
    #define EXTERN extern
#endif

EXTERN int variable;

#endif

```
In Main.c:
```

#define MAIN

#include "MyHeader.h"
...

```
In other modules:
```

#include "MyHeader.h"
...

```

---

### Post by IAMTubby on 2012-09-18
> 
In previous projects I've supported, I wrote header files with something like this:
```

#ifndef MY_HEADER_H
#define MY_HEADER_H

#ifdef MAIN
    #define EXTERN
#else
    #define EXTERN extern
#endif

EXTERN int variable;

#endif

```
In Main.c:
```

#define MAIN

#include "MyHeader.h"
...

```
In other modules:
```

#include "MyHeader.h"
...

```
dwhitney, I think I got this part.
So in main,
```

extern int a;

```
would translate to
```

int a;

```

correct ?

> **dwhitney67 said:**
> A variable has to be declared somewhere; only after it has been declared can you declare it elsewhere using 'extern'.

Sir, can you repeat this part once again. I couldn't get why you cannot "define" it inside main. What is the reason for the rule ?

---

### Post by dwhitney67 on 2012-09-18
> **IAMTubby said:**
> dwhitney, I think I got this part.
So in main,
```

extern int a;

```
would translate to
```

int a;

```
correct ?

Sir, can you repeat this part once again. I couldn't get why you cannot "define" it inside main. What is the reason for the rule ?
The variable has to be declared somewhere; you can do this in the module that has the main() function, or you can do it within a header file, or even another module.  Space is allotted on the stack for the variable; when the 'extern' is specified, no additional space is used.

Only as a last resort should variables be declared globally; good s/w developers avoid using 'extern'.

---

### Post by IAMTubby on 2012-09-18
So can we summarize that you declare extern in these places.
a) In the module that has the main
b) In one of the header files
c) But not inside main.

Sir, but why not inside main. What's the use of this limitation ?
I'm sorry, am I missing out an important point you are trying to make ?I keep troubling you with the same question again.

---

### Post by dwhitney67 on 2012-09-18
> **IAMTubby said:**
> 
c) But not inside main.

Sir, but why not inside main. What's the use of this limitation ?


There's a "special" region of the stack where global variables are stored.  When a variable is declared inside the main() function (or some other function), it is local to that function only.

You should not be dwelling on this topic too much.  As I stated earlier, usage of 'extern' oftentimes is a tell-tale sign of a poor design.

If you have a variable that is declared in a function, and you need another function to be aware of this value, then pass the variable either as a copy or as a pointer to that other function.

---

### Post by IAMTubby on 2012-09-18
Ok thanks a lot Sir.
Will make sure not to use it.

---

