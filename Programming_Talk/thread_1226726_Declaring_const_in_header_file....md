---
title: "Declaring const in header file..."
date: 2009-07-29
forum: Programming Talk
---

### Post by juzzbott on 2009-07-29
Hey all, 

I did a quick search on the net, and couldn't really see how to do this, other than using the #define preprocessor command.

I have the following 2 files:

generate.c
```
#include <stdio.h>
#include <stdlib.h>

/* Create the const variables */
const int DEFAULT_P_LEN = 8;
const int DEFAULT_NUM_P = 5;


/* The Generate Password function */
void generate(int p_len, int p_strength) {

    // If the length passed to the function is 0, set to the default.
    if (p_len == 0) {
        p_len = DEFAULT_P_LEN;
    }
    
    return;

}

```generate.h
```
#ifndef GENERATE_H_INCLUDED
#define GENERATE_H_INCLUDED



#endif // GENERATE_H_INCLUDED

/* generate password prototype */
void generate(int p_len, int p_strength);
```If I try and place the 2 consts into the generate.h file
```
#ifndef GENERATE_H_INCLUDED
#define GENERATE_H_INCLUDED



#endif // GENERATE_H_INCLUDED

/* Create the const variables */
const int DEFAULT_P_LEN = 8;
const int DEFAULT_NUM_P = 5;

/* generate password prototype */
void generate(int p_len, int p_strength);

```I get the following compiler error: > error: 'DEFAULT_P_LEN' undeclared (first use in this function).

So I can assume that the const in the header file is not being used, but I thought the #include "generate.h" file would include this?

Could I please get a little help on this please. 

EDIT: --- MUST INCLUDE generate.h FOR IT TO BE INCLUDED. Silly Me

Cheers, 
Justin

---

### Post by pepperphd on 2009-07-29
In the header file, declare your constants like this:

```

extern const int FOO;
extern const int BAR;

```

and in the .c(pp) file:

```
const int FOO = 42;
const int BAR = FOO * FOO;
```

In the files that need these, include the .h.

---

### Post by dribeas on 2009-07-30
> **pepperphd said:**
> In the header file, declare your constants like this:

```

extern const int FOO;
extern const int BAR;

```

and in the .c(pp) file:

```
const int FOO = 42;
const int BAR = FOO * FOO;
```

In the files that need these, include the .h.

The original question deals with C, and this answer is correct with respect to that language. Now, when it comes to C++ the compiler will deal correctly with the original code as the linkage rules for constants changed to allow for real compile time constants (that are not #defines). In fact in C++ the original code is better for exactly the same reason: the constant if defined in the header without the extern keyword is a compilation time constant rather than a runtime constant. The compiler can optimize using the value (say loop unrolling, for example).

---

### Post by Sockerdrickan on 2009-07-30
Yes using **const int name=42;** in headers is both enough and better.

---

