---
title: "Need extern explaination"
date: 2011-03-30
forum: Programming Talk
---

### Post by safarin on 2011-03-30
Hi,
I just practice C programming. I try to build a program with header and got a problem.

```

//main.c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#include "randdouble.h"

int main()
{
	srand(time(NULL));
	printf("%2.2f\n", randfrom(0,40));
	return 0;
}

```

```

//randdouble.c
#include <stdio.h>
#include <stdlib.h>

/* generate a random floating point number from min to max */
double randfrom(double min, double max) 
{
    double range = (max - min); 
    double div = RAND_MAX / range;
    return min + (rand() / div);
}

```

```

//randdouble.h

extern double randfrom(double min, double max);

```

and compile with this

```

gcc -Wall -o main main.c

and get this error
/tmp/cccM4GOz.o: In function `main':
main.c:(.text+0x2d): undefined reference to `randfrom'
collect2: ld returned 1 exit status


```

I don't understand why I get this error? Am I doing something wrong somewhere? Did gcc doesn't support extern? 

When I change #include "randdouble.h" to "randdouble.c" it success. But I want to include header file. I need some explanation, before this I used this extern method on fujitsu chip using Windows IDE and it success. I have very little experience in programming. 

Please help, thank you. :D

---

### Post by dwhitney67 on 2011-03-30
You also have to compile (and link object file) of the module in which you implemented randfrom().

For example:
```

gcc main.c randdouble.c -o main

```

P.S.  Remove unnecessary header files from your modules.  Also consider defining/implementing a function called randinit(), which calls srand(), within randdouble.h/.c.  Putting the srand() call in your main() function is lame.

---

### Post by safarin on 2011-03-30
> **dwhitney67 said:**
> You also have to compile (and link object file) of the module in which you implemented randfrom().

For example:
```

gcc main.c randdouble.c -o main

```

P.S.  Remove unnecessary header files from your modules.  Also consider defining/implementing a function called randinit(), which calls srand(), within randdouble.h/.c.  Putting the srand() call in your main() function is lame.

Hi dwhitney67, I remembered you. 
You are the one who help me to grab the concept of posix shared memory thing. Thank you again.

Ohh.. I thought when we called header in the main function, we doesn't need to link all the .c files. So that's mean my extern doesn't have any problem.
But why, when I included .c file in the main file (eg: #include "randdouble.c"), I just can compile without need to link .c file to the compiler??

P.S. Thank you for your suggestion about srand() and header, will proceed with it.

---

### Post by dwhitney67 on 2011-03-30
> **safarin said:**
> 
But why, when I included .c file in the main file (eg: #include "randdouble.c"), I just can compile without need to link .c file to the compiler??


Although what you have stated above can be done, it is not typical to see.  One of the (major) reasons it is not done is because there may be more than one module in a project that requires usage of the function(s) in a module.  Having each of these include the particular .c file wastes compiler time.

---

### Post by safarin on 2011-03-30
Thank you dwhitney67 for your wise explanation. You such a good teacher. Problem solved! :D

---

