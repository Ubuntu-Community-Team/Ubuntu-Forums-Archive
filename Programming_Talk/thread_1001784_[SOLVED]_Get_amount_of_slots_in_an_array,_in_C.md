---
title: "[SOLVED] Get amount of slots in an array, in C?"
date: 2008-12-04
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-04
The array I got is allocated with malloc().

And sizeof(array) gives always 4. How to do it?

---

### Post by dwhitney67 on 2008-12-04
If you have allocated the array (using malloc or calloc), there is not a way to determine the array's size.  Presumably, though you know the size because you specified it in the malloc() call.

If, however, you have an array created on the stack, then you can use division.

For example:
[php]
int array[10];

printf("size of array = %d\n", sizeof(array) / sizeof(int));
[/php]

---

### Post by crazyfuturamanoob on 2008-12-04
> **dwhitney67 said:**
> If you have allocated the array (using malloc or calloc), there is not a way to determine the array's size.  Presumably, though you know the size because you specified it in the malloc() call.

If, however, you have an array created on the stack, then you can use division.

For example:
[php]
int array[10];

printf("size of array = %d\n", sizeof(array) / sizeof(int));
[/php]

That does not work, I tried it. The array contains structs. But this works:
```

sizeof(*array)

```
I don't know what it does or how it works but I just tried it and noticed it works.

---

### Post by dwhitney67 on 2008-12-04
> **crazyfuturamanoob said:**
> That does not work, I tried it. The array contains structs. But this works:
```

sizeof(*array)

```
I don't know what it does or how it works but I just tried it and noticed it works.

The code I posted previously does indeed work, however if you read carefully I stated that it would NOT work for an array that has been allocated.

The sizeof(*array) provides you with the size of the first element in the array.  The * merely is dereferencing the first slot of the array; it is the same as if you coded sizeof(array[0]).

So in summary, the sizeof(*array) provides you with the size of the structure (or whatever element you are using); it does NOT provide information on how many slots have been allocated.

[php]
#include <stdio.h>
#include <stdlib.h>

struct Node
{
  int          value;
  struct Node* next;
  struct Node* prev;
};

int main()
{
  struct Node* nodes = malloc(20 * sizeof(struct Node));

  printf("sizeof struct Node = %d\n", sizeof(struct Node));
  printf("sizeof struct Node = %d\n", sizeof(*nodes));

  return 0;
}
[/php]

---

### Post by crazyfuturamanoob on 2008-12-04
> **dwhitney67 said:**
> The code I posted previously does indeed work, however if you read carefully I stated that it would NOT work for an array that has been allocated.

The sizeof(*array) provides you with the size of the first element in the array.  The * merely is dereferencing the first slot of the array; it is the same as if you coded sizeof(array[0]).

So in summary, the sizeof(*array) provides you with the size of the structure (or whatever element you are using); it does NOT provide information on how many slots have been allocated.

[php]
#include <stdio.h>
#include <stdlib.h>

struct Node
{
  int          value;
  struct Node* next;
  struct Node* prev;
};

int main()
{
  struct Node* nodes = malloc(20 * sizeof(struct Node));

  printf("sizeof struct Node = %d\n", sizeof(struct Node));
  printf("sizeof struct Node = %d\n", sizeof(*nodes));

  return 0;
}
[/php]

I'm talking about **arrays**, not linked lists this time.

I allocated the array like this:
```

int size_of_array = 10;
struct thing *w;
w = malloc( size_of_array * sizeof(struct thing) );

```
And I use it just like a normal array.

Edit:
Solved. I use an integer to hold the number of elements instead of trying to check it.

---

### Post by dwhitney67 on 2008-12-04
> **crazyfuturamanoob said:**
> I'm talking about **arrays**, not linked lists this time.

I allocated the array like this:
```

int size_of_array = 10;
struct thing *w;
w = malloc( size_of_array * sizeof(struct thing) );

```
And I use it just like a normal array.

Your code above is correct, however taking the sizeof(*array) will provide you with the size of "struct thing".  If the size of this struct is 10 bytes, then that would explain why you think you are getting the number of slots.  Allocate a 1000 slots and I bet your sizeof results will remain the same.

---

