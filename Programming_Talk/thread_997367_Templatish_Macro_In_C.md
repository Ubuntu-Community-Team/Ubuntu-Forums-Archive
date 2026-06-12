---
title: "Templatish Macro In C"
date: 2008-11-29
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-11-29
I am working on a 2D engine in C. To do Dimensional stuff you need vectors. I made a Vector library to do 2D manipulation of vectors, and I allowed the programmer to choose the precision of the components by using macros.

[PHP]typedef struct Vector {
	VECTOR_COMPONENT_TYPE x;
	VECTOR_COMPONENT_TYPE y;
} Vector;[/PHP]

I thought that maybe the programmer might want two different precision vectors (float, int, double, etc). Would it be a good idea to remove the protecting macros:
[PHP]#ifndef VECTOR_H
#define VECTOR_H
...
#endif[/PHP]
And allow the programmer to change the name of the Vector struct by using macros and then change the VECTOR_COMPONENT_TYPE.

Such that this CPP code
[PHP]#include "Vector.h"
#define VEC_NAME Vector_Double
#define VECTOR_COMPONENT_TYPE double
#include "Vector.h"[/PHP]

Would give two different vector structs, one with the standard precision (called Vector) and another with double precision (called Vector_Double)

Hope I am clear!

---

### Post by Mr.Macdonald on 2008-11-29
If my question confuses you, please respond!

Also if you like this idea and would like to expand on it please do so

---

### Post by slavik on 2008-11-30
the above will give an error/warning about redefining struct Vector. also when you use typedef like that, you don't have to use a tag.

you can also create a macro that defines a new vector for you like so:

#define MAKE_VECTOR(COMP_X, COMP_Y, NAME) typedef struct { COMP_X x; COMP_Y y; } NAME

and to use: MAKE_VECTOR(double,double,MyVector);
MyVector becomes a var of type struct {double x; double y;}

---

### Post by stroyan on 2008-11-30
If you use a macro you could use ## to concatenate a macro parameter with other strings to produce types and function names.
That makes it simpler to match up the types and names.
I am not really a fan of code that is obscured by deep macros.
It makes the code more difficult to read and to debug.
```

#define DECLARE_VECTOR(VECTOR_COMPONENT_TYPE) \
/*#define VECTOR_TYPE Vector_of_##VECTOR_COMPONENT_TYPE */\
 \
typedef struct { \
    VECTOR_COMPONENT_TYPE x; \
    VECTOR_COMPONENT_TYPE y; \
} Vector_of_##VECTOR_COMPONENT_TYPE; \
 \
Vector_of_##VECTOR_COMPONENT_TYPE sum_##VECTOR_COMPONENT_TYPE##_vector( \
    Vector_of_##VECTOR_COMPONENT_TYPE a, \
    Vector_of_##VECTOR_COMPONENT_TYPE b);

``````

#include <vector.h>

/* Define float type */
DECLARE_VECTOR(float)
/* Define double type */
DECLARE_VECTOR(double)

void use()
{   
    Vector_of_float F1, F2;
    Vector_of_double D1, D2;
    
    F1 = sum_float_vector(F1, F2);
    D1 = sum_double_vector(D1, D2);
}

```

---

