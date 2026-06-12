---
title: "Array deferencing versus pointer deferencing"
date: 2009-08-29
forum: Programming Talk
---

### Post by soltanis on 2009-08-29
Consider the example of a pointer to a two dimensional array of integer.

```

int (*ptwobytwo)[2][2];

```
EDIT: the parenthesis added because of weak binding of the * operator.

This concept is distinct from, say, a pointer to a pointer to a pointer to an integer:

```

int ***pppi;

```

Because in the first example, I have allocated (one assumes) the storage for the array, and furthermore if I access the array itself:

```

twobytwo[1][1];

```

The compiler will do 2x1+1 = element 3, the last element of the array, as opposed to

```

pppi[1][1][1];

```

The compiler here does the first pointer + 1, the second pointer + 1, then the third pointer + 1.

My question here is:

what if I mix the two? In other words, is writing this:

```

ptwobytwo[0][1][1];
/// the same as this:
(*ptwobytwo)[1][1];

```

Shouldn't the compiler for the first line deference the first pointer, arrive at a two by two array, then do 2x1 + 1 = element 3 of the array?

---

### Post by smartbei on 2009-08-29
A simple test usually works:
```

#include <cstdio>


int main(void)
{

	int arr[2][2] = {{1,2},{3,4}};
	int *parr[2][2];

	printf("1: %d\n", (*parr)[1][1]);
	printf("2: %d\n", parr[0][1][1]);

	return 0;
}

```
That compiles and works for me - it looks like you can indeed use [0] to dereference (which makes sense).

---

### Post by dribeas on 2009-08-29
The whole question is a little confusing. So I will work from concepts up.

First, in C, when you write x[y] and either x or y is a pointer (or can decay into a pointer) and the other is an integer value, the compiler will translate the code into *( x + y ). The compiler, furthermore will perform the pointer algebra considering the size of the data pointed to.

```

int (*p)[2][2]; // p is a pointer into a 2x2 integer array:

p[0][1][1] = 5; // => (*(p+0))[1][1] => (*p)[1][1]

```

This can be easily tested:

```

// test.cpp
void print( int const (&array)[2][2] )
{
   std::cout << array[0][0] << " " << array[0][1] 
       << " / " << array[1][0] << " " << array[1][1] << std::endl;
}
int main()
{
   int array[2][2] = {}; // value initialized
   print( array ); // 0 0 / 0 0
   int (*p)[2][2] = &array;
   (*p)[1][1] = 1;
   print( array ); // 0 0 / 0 1
   p[0][1][1] = 2;
   print( array ); // 0 0 / 0 2
   0[p][1][1] = 3;
   print( array ); // 0 0 / 0 3
}

```

I hope this helps.

---

### Post by soltanis on 2009-08-29
Right -- the problem I had was the *distinction* between an array and a pointer. Specifically multi-dimensional arrays and pointers to pointers. It all makes better sense this way:

```

ptwobytwo[0][2][2] = 3; // <==> *(*(ptwobytwo + 0) + 2 * 1 + 2) = 3;

```

Although you have to bear in mind that subtle distinction between a pointer and an array.

---

### Post by dribeas on 2009-08-30
> **soltanis said:**
> Right -- the problem I had was the *distinction* between an array and a pointer. Specifically multi-dimensional arrays and pointers to pointers. It all makes better sense this way:

```

ptwobytwo[0][2][2] = 3; // <==> *(*(ptwobytwo + 0) + 2 * 1 + 2) = 3;

```

Although you have to bear in mind that subtle distinction between a pointer and an array.

The distinction is not subtle at all. An array can decay into a pointer to the address of the first element of the type, and you can dereference with the [] operator in both cases, with the semantics already discussed, but they are quite different.

Consider:
```

int x = 1, y = 1, z = 1;
int array3d[2][2][2];
array3d[x][y][z] = 1; // 1
int ***ptr = allocate_2by2by2(); // moved the complexity into a function for discussion purposes
ptr[x][y][z]; // 2
[CODE]

In (1) the compiler takes the address of the beginning of the contiguous memory allocated to array3d and calculates the offset from there:

[CODE]
// equivalent code for 1
int* base = & array[0][0][0];
*(base + (4* x + 2* y + z ) ) = 1;

```

On the other hand, in (2) the compiler is doing:

```

*(*(*(ptr+x) + y) +z) = 1;
// ptr is of type int***
// *(ptr+x) is of type int**
// *(*(ptr+x)+y) is of type int*
// *(*(*ptr+x)+y+z) is of type int

```

As you can see the difference is notable, in the first case, the compiler calculates an offset after the first pointer, adds it to the initial address and dereferences only once (memory must be contiguous). In the second case, the compiler is performing pointer arithmetic and dereferencing for each and all [] operations. In this case, the memory does not need to be contiguous.

The key there is that applying operator[] to a pointer type will perform pointer arithmetic and return an element of the pointed to type. In the second case, the pointed type is int**.

In your first question, you only had a pointer indirection, and in that particular case, the pointed type was int[2][2] and the compiler worked the offset from there on in the same terms it would have done with an array, but that works only in specific cases.

---

