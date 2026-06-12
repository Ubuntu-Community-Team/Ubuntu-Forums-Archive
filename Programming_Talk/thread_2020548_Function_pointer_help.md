---
title: "Function pointer help"
date: 2012-07-08
forum: Programming Talk
---

### Post by spanlength1 on 2012-07-08
Hi , I am starting with my assignment which is based on function pointers and need some help and clarity to implement them. Please provide some inputs which will help me in implementing them

```

#ifndef TKK_AS_C_FILTER_H
#define TKK_AS_C_FILTER_H

/* Predicate (a function returning a boolean value) that tests if a given function is linear
 * Parameter: A function pointer that returns a double and has one double parameter
 * Returns: 0 for non-linear functions
 *          != 0 for linear functions
 * Hint: See the given main.c for four examples of parameter functions */
int isLinear(/* TODO: TYPE */);

/* Same as isLinear but for quadratic functions */
int isQuadratic(/* TODO: TYPE */);

/* Filter a NULL terminated array of function pointers
 * Returns a new dynamically allocated array of function pointers that contains
 *  only the function pointers in the parameter array for which the parameter
 *  predicate is true.
 * Parameters: An array of functions (same kind of functions that the predicates
 *                                    accept, i.e. l1, l2, etc.
 *             A predicate (isLinear, isQuadratic or similar) */
/* TODO: TYPES */ filterFunctions;

#endif
```
```

#include <stdio.h>
#include <stdlib.h>

#include "filter.h"

/* Two linear and two quadratic functions */
static double l1(double p)
{
  return 2 * p + 1;
}

static double l2(double p)
{
  return -p + 3;
}

static double q1(double p)
{
  return 3 * p * p - 4 * p - 5;
}

static double q2(double p)
{
  return -2 * p * p + 5.5 * p + 1;
}

const char* nameFunction(/* TODO: TYPE */ f)
{
  if (f == l1)
    return "l1";
  if (f == l2)
    return "l2";
  if (f == q1)
    return "q1";
  if (f == q2)
    return "q2";
  return "unknown";
}

/* A some-assembly-required(tm) main() function.
 * Add the missing function pointer types. */
int main(void)
{
  /* TODO: TYPE */ arr[5] = {l1,q1,l2,q2, NULL};
  /* TODO: SAME TYPE AS BEFORE */  *arrLinear, *arrQuadratic;

  arrLinear = filterFunctions(arr, isLinear);
  arrQuadratic = filterFunctions(arr, isQuadratic);
  
  printf("arrLinear:");
  for (size_t i = 0;arrLinear[i];i++)
    printf(" %s", nameFunction(arrLinear[i]));
  printf("\narrQuadratic:");
  for (size_t i = 0;arrQuadratic[i];i++)
    printf(" %s", nameFunction(arrQuadratic[i]));
  printf("\n");
  free(arrLinear);
  free(arrQuadratic); 
}
```

Please share your inputs and how to determine if a function is linear or quadratic ?

---

### Post by dwhitney67 on 2012-07-08
Try something like:
```

const char* nameFunction(double (*f)(double))

```

---

### Post by ofnuts on 2012-07-09
> **spanlength1 said:**
> Please share your inputs and how to determine if a function is linear or quadratic ?

[http://en.wikipedia.org/wiki/Linear_function](http://en.wikipedia.org/wiki/Linear_function)
[http://en.wikipedia.org/wiki/Quadratic_function](http://en.wikipedia.org/wiki/Quadratic_function)

---

### Post by spanlength1 on 2012-07-09
> **ofnuts said:**
> [http://en.wikipedia.org/wiki/Linear_function](http://en.wikipedia.org/wiki/Linear_function)
[http://en.wikipedia.org/wiki/Quadratic_function](http://en.wikipedia.org/wiki/Quadratic_function)

Well I have done some modifications in filter.h and fiter.c and created the basic skeleton for implementation. I want to know if this ok or not. 
```

#ifndef TKK_AS_C_FILTER_H
#define TKK_AS_C_FILTER_H
#include <stdlib.h>
#include <stdio.h>
#include <stddef.h>

typedef double(*myfunc)(double);
typedef int(*afunc)(myfunc);

int isLinear(myfunc func);

int isQuadratic(myfunc func1);

 * Parameters: An array of functions (same kind of functions that the predicates
 *  accept, i.e. l1, l2, etc.
 *  A predicate (isLinear, isQuadratic or similar) */

myfunc filterFunctions(myfunc[],afunc);

#endif

```

I need some clarification whether the filterFunctions signature is ok or not.
```


#include <stdio.h>
#include "filter.h"
#include <stdlib.h>


int isLinear(myfunc func){
    
}

int isQuadratic(myfunc func1){
    
}

myfunc filterFunctions(myfunc[],afunc){

}

```

here I get error on the filterFunctions that 
filter.c:14:1: error: parameter name omitted. 

Please sujjest what needs to be modified.

And finally the main.c is also modified. 
```
#include <stdio.h>
#include <stdlib.h>
#include <stddef.h>
#include "filter.h"

/* Two linear and two quadratic functions */
static double l1(double p)
{
  return 2 * p + 1;
}

static double l2(double p)
{
  return -p + 3;
}

static double q1(double p)
{
  return 3 * p * p - 4 * p - 5;
}

static double q2(double p)
{
  return -2 * p * p + 5.5 * p + 1;
}

const char* nameFunction(myfunc f1)
{
  if (f1 == l1)
    return "l1";
  if (f1 == l2)
    return "l2";
  if (f1 == q1)
    return "q1";
  if (f1 == q2)
    return "q2";
  return "unknown";
}

/* A some-assembly-required(tm) main() function.
 * Add the missing function pointer types. */
int main(void)
{
	
  myfunc arr[5] = {l1,q1,l2,q2, NULL};
  myfunc *arrLinear, *arrQuadratic;

  arrLinear = filterFunctions(arr, isLinear);
  arrQuadratic = filterFunctions(arr, isQuadratic);
  
  printf("arrLinear:");
  for (size_t i = 0;arrLinear[i];i++)
    printf(" %s", nameFunction(arrLinear[i]));
  printf("\narrQuadratic:");
  for (size_t i = 0;arrQuadratic[i];i++)
    printf(" %s", nameFunction(arrQuadratic[i]));
  printf("\n");
  
  free(arrLinear);
  free(arrQuadratic); 
}

```

Please review the code and i will start with the implementation.

---

### Post by trent.josephsen on 2012-07-09
> **spanlength1 said:**
> 
```

typedef double(*myfunc)(double);
typedef int(*afunc)(myfunc);
```

Don't overuse typedef. The long form is more informative and your most complicated declaration is

```
myfunc filterFunctions(myfunc[],afunc);
```

In this case it's probably warranted to typedef the first one (although I'd **suggest** a name like "polynomial" instead of "myfunc" which tells the reader next to nothing), because with filterFunctions you pass those around and make arrays of them and so forth without actually calling them. But the second typedef just hides information.

As for filterFunctions, it needs to yield an array of polynomials, not just one, so you need to make it return a pointer.

```
/* here, it's useful to know the exact type of the function pointer parameter */
int isLinear( double (*)(double) );
int isQuadratic( double (*)(double) );

/* here, calling the function pointer "polynomial" tells you more about its role in the program */
typedef double (*polynomial)(double);
polynomial *filterFunctions( polynomial[], int (*)(polynomial) );
```

Finally, what part of "parameter name omitted" didn't you understand? You can *declare* a function without naming the parameters (like I've done above), but you can't *define* it that way or you don't have any way to use them.

```
polynomial *filterFunctions( polynomial arr[], int (*cmp)(polynomial) )
{
    /* code goes here and uses arr and cmp */
}
```

---

