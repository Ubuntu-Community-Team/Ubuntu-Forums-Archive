---
title: "[SOLVED] [C] Custom operators?"
date: 2008-03-20
forum: Programming Talk
---

### Post by Can+~ on 2008-03-20
I was given this "bonus" task at university, about building home-made complex numbers. So far so good, I could do everything on the task (sum and multiplication).

Now I'm wondering, if it's possible that I could do something like, building my own operators for this struct, like "complex a + complex b".

[PHP]typedef struct
{
	float r,i;
}complex;

// blah blah...
complex a, b;

//the user fills a and b with something like:
// a = 2+3i
// b = 4-6i
c = a + b

//And c should be 6-3i[/PHP]

C is kinda awkward after months with python+gtk.

PD: The task is finished, it could be sent right now, but I'm wondering if this is possible.

---

### Post by eye208 on 2008-03-20
> **Can+~ said:**
> Now I'm wondering, if it's possible that I could do something like, building my own operators for this struct, like "complex a + complex b".
It's possible in C++, but not in C.

---

### Post by pmasiar on 2008-03-20
C does not have operator overloading, the only way is to call function: complex_add(complex_x, complex_y)

---

### Post by jpkotta on 2008-03-20
C99 has a complex type.

```

#include <complex.h>
#include <stdio.h>

int main(void)
{
    complex z = 1+2*I;
    z *= z;

    printf("z squared is (%f + j*%f).\n",
	   creal(z), cimag(z));
    
    return 0;
}

```

```

[jpkotta@gauss w](1)$ gcc -o complex complex.c 

[jpkotta@gauss w](1)$ ./complex 
z squared is (-3.000000 + j*4.000000).

```

But in general, you can't do operator overloading like the others said.

---

