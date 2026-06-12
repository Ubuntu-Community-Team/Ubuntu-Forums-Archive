---
title: "Pointer which can point to any variable type, in C?"
date: 2008-12-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-22
As I know, a pointer is a variable which contains a memory address.

And every variable has an address. The addresses don't differ by size,
so why there couldn't be a pointer which can point to ANYTHING?

I just want a pointer which can point to either integer, a struct, NULL, or everything.


Thanks.

---

### Post by dwhitney67 on 2008-12-22
Use a void*.

Now, I do not recommend that you use void* in lieu of a pointer to an actual data type, if you know the type ahead of time, but in certain cases using void* is helpful.

P.S.  When using a void*, you will not be able to perform arithmetic operations on the pointer.

---

### Post by crazyfuturamanoob on 2008-12-22
> **dwhitney67 said:**
> Use a void*.

Now, I do not recommend that you use void* in lieu of a pointer to an actual data type, if you know the type ahead of time, but in certain cases using void* is helpful.

P.S.  When using a void*, you will not be able to perform arithmetic operations on the pointer.

Arimetric operations?

Please no complicated explanations, I'm bad at maths.

---

### Post by dwhitney67 on 2008-12-22
Maybe this example program will help you understand:
[php]
#include <stdio.h>

int main()
{
  int array[5] = { 1, 2, 3, 4, 5 };

  int* pa = array;

  for (int i = 0; i < 5; ++i, ++pa)
  {
    printf("%d ", *pa);
  }
  printf("\n");


  void* va = array;   // legal statement 

  // but can't use arithmetic operation with va, nor can it be
  // accessed as if an array
  /*
  for (int i = 0; i < 5; ++i, ++va)
  {
    printf("%d ", *va);
  }
  for (int i = 0; i < 5; ++i)
  {
    printf("%d ", (int)va[i]);
  }
  printf("\n");
  */

  return 0;
}
[/php]

---

### Post by Npl on 2008-12-22
> **crazyfuturamanoob said:**
> Arimetric operations?

Please no complicated explanations, I'm bad at maths.Hope you arent offended, but I find this answer funny :)

it means merely you cant add/substract from a void pointer, you can add/substract with other pointers
```
int array[5]={10,20,30,40,50};
int *ptr = array;
int i;

i = *(ptr + 0); // same as i = ptr[0];
ptr += 2; // same as ptr = &ptr[2];
i = *ptr; // i is now = 30

```

For that to work the compiler needs to know the size of an integer, 4 bytes in most cases. void has no size, thus it wont work

---

