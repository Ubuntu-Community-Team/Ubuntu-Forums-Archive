---
title: "&quot;Begining Programming&quot; by kingsly-hughes"
date: 2008-01-21
forum: Programming Talk
---

### Post by gimfred on 2008-01-21
I have been trying to teach myself C++ after 3 or 4 stops and starts in other languages (lisp, python, C#). I have been following Kingsley-Hughes "Beginning Programming". 

(I recommend it even though some of the commands apparently are a little out of date -- every function is ```
void *functionname*();
``` instead of ```
int *functionname();*
``` I'm told that "void functioname()" is depreciated for defining a function.) 


So far I have been feeling very successful, at least until I got Chapter 10 - Interface. 

Now I can type in the program on pages 262 and 263 and it works, but I wanted to change the code around a little to be able to do more than a single calculator at a time. My version of their code either goes into an infinite loop or calls functions before they have been defined.

I've tried various C++ tutorials/manuals but everything is talking over my head. [http://www.openbookproject.net//thinkCS/cpp/english/index.htm](http://www.openbookproject.net//thinkCS/cpp/english/index.htm), [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/), and [http://www.parashift.com/c++-faq-lite/](http://www.parashift.com/c++-faq-lite/) have all been tried amongst others that are much poorer quality/harder to comprehend.

I have tried moving main(); to the top of the code, which still calls calc() and helpsys() before they are defined. I have tried changing ```
int calc()
     {

     }
``` 
to 
```
void calc();

int main()
     {
  
     }

int calc()
     {

     }

```

which just generates an "ambiguates old declaration" error,

I have tried changing 
```
int calc()
     {

     }
```
to ```

void calc()
      {

      }
```

I have also changed the "return main();" to "return 1;" I don't want a return 0; as that exits. 

Does anyone know where I might find a simple explanation of what I need to do to fix my menu system? Or even better point out my logic fault (other than calling functions before being defined)!

Here is "Beginning Programming"'s code (calctest.txt) and mine (calcapp.txt). If someone can head me off in the correct direction, well, I'll go out of my way to do something real nice for someone else.

I also though I would be able to declare all the variables for the program in main() but doesn't work I have found out. 
* I love compiling! *

---

### Post by LaRoza on 2008-01-22
> **gimfred said:**
> 
(I recommend it even though some of the commands apparently are a little out of date -- every function is ```
void *functionname*();
``` instead of ```
int *functionname();*
``` I'm told that "void functioname()" is depreciated for defining a function.) 



0. void is acceptable as a return value (actually, it won't return anything) but not for main(). 

1. Look into function prototypes.

2. main should return 0. Don't use recursion for this. Use a loop.

---

### Post by geraldm on 2008-01-22
Use a header file to declare the function prototype (avoid undefineds)

file calc.h ---
#ifndef CALC_H
#define CALC_H
int calc;
#endif
fileend calc.h ---

Add this at the beginning of calc.cpp
#include "calc.h"

OTHER RULES:
do not call a function from within the same function.
This is OK when programming recursive functions, but only then is it OK (sometimes)
so remove commands calling calc from within calc; and main from within main();

Logic changes:
from within main:
  while (1) // loop forever {
  offer help(), quit(), calc()
  }

for temporarily, always return to main from calc()
This allows the user to access the help().

In main()
  add "cin >> operand;" before operand is used in conditional statements.

Good luck on your programming start.

Gerald

---

### Post by gimfred on 2008-01-22
> **geraldm said:**
> Use a header file to declare the function prototype (avoid undefineds)

file calc.h ---
#ifndef CALC_H
#define CALC_H
int calc;
#endif
fileend calc.h ---

Add this at the beginning of calc.cpp
#include "calc.h"

OTHER RULES:
do not call a function from within the same function.
This is OK when programming recursive functions, but only then is it OK (sometimes)
so remove commands calling calc from within calc; and main from within main();

Logic changes:
from within main:
  while (1) // loop forever {
  offer help(), quit(), calc()
  }

for temporarily, always return to main from calc()
This allows the user to access the help().

In main()
  add "cin >> operand;" before operand is used in conditional statements.

Good luck on your programming start.

Gerald

Wow! I thought I was performing the correct recursion. eep. Thank you, to both the posts.

---

### Post by LaRoza on 2008-01-22
> **gimfred said:**
> Wow! I thought I was performing the correct recursion. eep. Thank you, to both the posts.

Recursion can be useful, but only in a few situations and different languages are better at it.

---

