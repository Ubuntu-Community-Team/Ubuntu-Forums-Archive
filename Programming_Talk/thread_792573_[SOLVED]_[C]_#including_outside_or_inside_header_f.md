---
title: "[SOLVED] [C] #including outside or inside header file?"
date: 2008-05-13
forum: Programming Talk
---

### Post by nvteighen on 2008-05-13
Hi again!
I was trying to do Programming Challenge 10 ([http://ubuntuforums.org/showthread.php?p=4891535](http://ubuntuforums.org/showthread.php?p=4891535)) by creating a shared library that set a custom data type up and devised basic arithmetic functions for that data type. [OK, it works, but only for positive addition and substraction... sadly, I couldn't finish the rest of the challenge]

My question is on the header file I created for using the library. I need the FILE * data type for one function prototype, so should I #include <stdio.h> inside the header or in .c source codes?

Here are the sources (not for the library itself... PM me if you want to take a look on it):

float.h
[PHP]
/*
 *float.h: Header file for my library
 */
#include <stdio.h> /*<--???*/

typedef struct NewFloat exact_float_t;

extern exact_float_t *floatSetFloat(const char *RawFloat);
extern void floatFreeFloat(exact_float_t *Float);
extern void floatPrintFloat(FILE *File, exact_float_t *Float);
extern void floatSum(exact_float_t *FloatA, exact_float_t *FloatB, exact_float_t *Sum);
extern void floatSubstract(exact_float_t *FloatA, exact_float_t *FloatB, exact_float_t *Res);
[/PHP]

main_float.c
[PHP]
/*
 *main_float.c: A sample program using my float library
 */

/*#include <stdio.h>???*/
#include "float.h"

int main(void)
{
	exact_float_t *Float = floatSetFloat("9.789786");
	exact_float_t *AnotherFloat = floatSetFloat("3929292.523737");
	exact_float_t *SumFloat = floatSetFloat("0.0");

	floatSubstract(AnotherFloat, Float, SumFloat);

	floatPrintFloat(stdout, SumFloat);

	floatFreeFloat(Float);
	floatFreeFloat(AnotherFloat);
	floatFreeFloat(SumFloat);

	return 0;
}
[/PHP]

Thanks!

---

### Post by slavik on 2008-05-13
there is no problem with including other header files in your header files. :)

---

### Post by nvteighen on 2008-05-13
> **slavik said:**
> there is no problem with including other header files in your header files. :)
I know, but it may lead to code duplication if (in the very hypothetical case someone else used this library) somone also #include <stdio.h> in the .c in order to use printf(), for example.

In other words, what's the best programming practice? Wouldn't be "safer" to tell people to always #include <stdio.h> in the C source before using "float.h"? Or is there a way to #include conditionally if a header has not been included yet (something like #ifndef...#endif)?

---

### Post by RIchard James13 on 2008-05-13
The header files should have guards around them so they can only get included once.

You place an "if not defined" followed by a define at the top of the header. Below any comments, like this:
[PHP]#ifndef ACTORCONTAINER_H
#define ACTORCONTAINER_H
[/PHP]

and at the end you place the end if statement like this
[PHP]#endif[/PHP]

This makes the preprocessor skip the file if has already processed it. The first time through it reads it in and the define declares ACTORCONTAINER_H. The next time it is included it skips the #ifndef #endif section because ACTORCONTAINER_H is already defined. ACTORCONTAINER_H is just a name I made up.

Normally I make the name of the define is the name of the file followed by _H all in uppercase. Sometimes different conventions are used to avoid collisions most variations revolve around placing the _ character before and after the name like _ALLOCA_H or __CAPICMD_H__ have a look at the files in /usr/include/

stdio.h already has a header guard _STDIO_H so you don't need to worry about it being included more than once.

---

### Post by irrdev on 2008-05-13
Placing enclosed "definition guards" around your header sources is almost mandatory to ensure no multiple-includes, but this method is also very costly in terms of resources. The compiler still has read each line of the header file until it reaches the #endif . Therefore, change your code to look like this:
```

#pragma once
#ifndef MAIN_C_HEADER
#define MAIN_C_HEADER

// Place your header source in here

#endif

```
The **#pragma once** rule is supported by most modern compilers such as gcc and VC++, and it explicitly instructs the compiler to only include the header file once. The compiler will never need to re-read the entire header file if it already has been included. If the compiler does not support this definition, then the more resource-costly "definition guards" will act as a fallback.

---

### Post by slavik on 2008-05-13
#pragma once is not part of a standard.

more info here: [http://en.wikipedia.org/wiki/Pragma_once](http://en.wikipedia.org/wiki/Pragma_once)

---

### Post by nvteighen on 2008-05-13
Thank you all!

This was really informative!

---

