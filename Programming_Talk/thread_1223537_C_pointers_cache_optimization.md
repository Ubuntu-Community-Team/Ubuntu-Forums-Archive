---
title: "C pointers cache optimization"
date: 2009-07-26
forum: Programming Talk
---

### Post by jero3n on 2009-07-26
I was reading a paper for cache optimization and spatial locality of data to get some ideas to optimize a piece of code and I have a question

Having a situation like this:
```
double a[X];
double b[X][Y];
```

When you access elements from a and b rightmost dimension often, I think it is better to have:
```
struct
{
 double a;
 double b[Y];
} c[X];
```
Right?

But, what happens if you have pointers instead of arrays? Does the following refactoring works in the same way?
```
double *a; // points to an array
double **b; // points to an array of arrays

 becomes:

struct
{
 double a;
 double *b;
} *c;
```
 Does the CPU knows that *b points to array data, so to prefetch in the second case?
Any suggestion for a good data structure optimization paper for C would be great :)
Thanks

---

### Post by jpkotta on 2009-07-26
I don't think the compiler knows a pointer is the head of an array unless you declare it as such.

This is not something I have dealt with.  But this is an excellent paper with a section about this very issue: [http://people.redhat.com/drepper/cpumemory.pdf](http://people.redhat.com/drepper/cpumemory.pdf).  Ulrich Drepper is the guy behind glibc.  Also, it is usually a good idea to have a single block of memory and use an indexing function to determine your array layout.  E.g., 
```

#define IDX(i,j) ((i)*10 + (j))
double *ten_by_ten = malloc(10*10*sizeof(double));
for (i=0; i < 10; i++) {
    for (j=0; j < 10; j++) {
        ten_by_ten[IDX(i,j)] = drand48();
    }
}

```
This way you don't have to remember which way the language orders dimensions, and you don't have a complicated data structure with lots of pointers.  Obviously, you will want to arrange by rows first or columns first depending on the application.

---

### Post by stair314 on 2009-07-26
I can't speak with certainty but I thought that memory cache pre-fetches are not determined by the compiler. In part they are determined by the physical cache hardware: the cache is divided into blocks that are fetched as one unit, so if you fetch one byte you also fetch everything else in the same block as it. Also, when your memory fills up and things start getting paged out to your swap disk, if you fetch one byte, you fetch everything on that page. The operating system might also try to guess that you'll want the next consecutive page as well.
I could be totally wrong though; maybe some compilers do try to prefetch things.
The one thing I am certain of is that the block/page structure will make sure that there is some benefit to spacial locality regardless of whether your C code uses array syntax or pointer syntax.

---

### Post by slavik on 2009-07-26
> **stair314 said:**
> I can't speak with certainty but I thought that memory cache pre-fetches are not determined by the compiler. In part they are determined by the physical cache hardware: the cache is divided into blocks that are fetched as one unit, so if you fetch one byte you also fetch everything else in the same block as it. Also, when your memory fills up and things start getting paged out to your swap disk, if you fetch one byte, you fetch everything on that page. The operating system might also try to guess that you'll want the next consecutive page as well.
I could be totally wrong though; maybe some compilers do try to prefetch things.
The one thing I am certain of is that the block/page structure will make sure that there is some benefit to spacial locality regardless of whether your C code uses array syntax or pointer syntax.
You are correct, but it is also possible to write code in such a way that will make the pre-fetching algorithm more accurate.

---

### Post by jero3n on 2009-07-27
> **jpkotta said:**
> But this is an excellent paper with a section about this very issue: [http://people.redhat.com/drepper/cpumemory.pdf](http://people.redhat.com/drepper/cpumemory.pdf).  Ulrich Drepper is the guy behind glibc.  


Indeed it seems an excellent paper and exactly what I was looking for. Thank you.

Regarding:
> #define IDX(i,j) ((i)*10 + (j))
I am not sure if multiply is faster than dereferencing, though it is good having data continuous. However cache misses arise when there are more than one arrays that accessed at once and I think this will not help much.

> **stair314 said:**
>  so if you fetch one byte you also fetch everything else in the same block as it.
I guess you are right, so arrays and pointers to arrays have the same cache behaviour.

Thanks :)

---

### Post by stroyan on 2009-07-27
There can be very important performance differences between
multidimensional arrays and arrays of pointers.

If you use pointers and multiple mallocs you can produce a
variable size data structure that can be accessed with much the
same source code as an array.
```

float **a;
a=(float **) malloc(sizeof(float *) * dim1);
for (i=0; i<dim1; i++) {
    a[i] = (float *) malloc(sizeof(float) * dim2);
    for (j=0; j<dim2; j++) {
    	a[i][j] = 0.0;
    }
    some_function(a);
}

```
But the compiler knows much less about the access pattern of
loops through that array.  If cannot prefetch some element a[i][j]
until it has already loaded the pointer a[i].  That is very different
from a single multidimensional array of a known size.  Accessing the
elements of a single array allows the compiler to predict all the
addresses of the array elements.  It can then prefetch those elements.
A loop that iterates through several values of the higher indices will be
much more likely to prefetch well if the array has known dimensions.

Many modern processors also have hardware prefetch mechanisms that will
keep notes and observe sequentices of memory accesses that occur at a
constant stride through memory.  Those may be able to detect and predict
more patterns than a compiler will catch in advance.  But they can only
see a pattern that is actually there.  A data structure allocated by
many malloc calls (or other memory allocation calls) may have an arbitrary
arrangement in process address space.

---

### Post by jpkotta on 2009-07-28
GCC has some arch-dependent ways to prefetch data into cache.  These exist in 4.3 and later.

[http://gcc.gnu.org/projects/prefetch.html](http://gcc.gnu.org/projects/prefetch.html)

---

### Post by jero3n on 2009-07-28
> **stroyan said:**
> 
If you use pointers and multiple mallocs you can produce a
variable size data structure that can be accessed with much the
same source code as an array.
But the compiler knows much less about the access pattern of
loops through that array.

I am a bit confused. Does this mean that if you keep the data continuous, you improve cache behavior? Or it is impossible in variable size arrays?

For example:
```

float **a = malloc(nrows * sizeof(float*));
a[0] = malloc(totalcells * sizeof(float));
for(i = 1; i < nrows; i++) 
  a[i] = a[i-1] + ncolumns[i-1];


```
Does this produces a cache aware variable size array?

---

### Post by stroyan on 2009-07-28
> **jero3n said:**
> I am a bit confused. Does this mean that if you keep the data continuous, you improve cache behavior? Or it is impossible in variable size arrays?

For example:
```

float **a = malloc(nrows * sizeof(float*));
a[0] = malloc(totalcells * sizeof(float));
for(i = 1; i < nrows; i++) 
  a[i] = a[i-1] + ncolumns[i-1];


```
Does this produces a cache aware variable size array?

I think you meant to initialize the "a" array like this.
```

totalcells = nrows*ncolumns;
float **a = malloc(nrows * sizeof(float*));
a[0] = malloc(totalcells * sizeof(float));
for(i = 1; i < nrows; i++) 
  a[i] = a[i-1] + ncolumns; /* (float *) sized pointer math */

```
That way the contents of the array are guaranteed to be tightly packed.
But the compiler will not be able to know that is true.
Even if it sees that in the initialization that information won't be available in functions that are passed the "a" array.
A reference to an array variable like v=a[i][j] will look like
float *p=a[i]; v=p[j]
The compiler will not be able to predict the address of "p[j]" and prefetch it.
So a loop like 
for (i=0;i<nrows;i++) a[i][i] += 1.0;
will not be able to explicitly prefetch the addresses for the diagonal because the compiler does not know that the contents of a[i] will always be at even intervals.
A hardware stride detection feature in a CPU may be able to prefetch those addresses.
They actually are at regular intervals.
Hardware prefetch mechanisms deal with the actual addresses used and predict based only those addresses rather then true foreknowledge of what will happen next.
I went looking for some good reference material to point you to.
But most of the material on this topic is in pay-to-read academic journals and books.
Here are a couple of OK discussions.
[http://suif.stanford.edu/papers/mowry92/subsection3_5_2.html](http://suif.stanford.edu/papers/mowry92/subsection3_5_2.html)
[http://books.google.com/books?id=7ZUl0WozEdoC&pg=PA311&lpg=PA311&dq=hardware+stride+prefetch&source=bl&ots=Mjuw3pO7aV&sig=ORYsQS2OTgd5WXYuyY7CrFk0r5Q&hl=en&ei=VjNvSqK6M5-ltgelvpXQCA&sa=X&oi=book_result&ct=result&resnum=8](http://books.google.com/books?id=7ZUl0WozEdoC&pg=PA311&lpg=PA311&dq=hardware+stride+prefetch&source=bl&ots=Mjuw3pO7aV&sig=ORYsQS2OTgd5WXYuyY7CrFk0r5Q&hl=en&ei=VjNvSqK6M5-ltgelvpXQCA&sa=X&oi=book_result&ct=result&resnum=8)

---

### Post by jero3n on 2009-07-28
> **stroyan said:**
> I think you meant to initialize the "a" array like this.
```

totalcells = nrows*ncolumns;
float **a = malloc(nrows * sizeof(float*));
a[0] = malloc(totalcells * sizeof(float));
for(i = 1; i < nrows; i++) 
  a[i] = a[i-1] + ncolumns; /* (float *) sized pointer math */

```

Yes, the only difference in my code is that each row has not the same number of columns, so there is no way to predict intervals. 

Thanks a lot, I think I have to read Ulrich Drepper's paper first, carefully. One thing that is not clear in my mind yet, is who is responsible for the pre-fetching, CPU internal or instructions generated by the compiler.

---

### Post by stroyan on 2009-07-28
Who prefetches will vary for different architectures and different compilers.  The x86 architecture has both hardware and software prefetching.  The ia64 architecture has only software prefetching.
Another point that could help prefetching is the use of c89 style variable size arrays.
gcc will allow you to use array parameters that have their size defined by other passed parameters, like this-
```

float sum(int rows, int columns, float a[rows][columns])
{
    float sum = 0.0f;
    int i, j;

    for (i=0; i<rows; i++) {
	for (j=0; j<columns; j++) {
	    sum += a[i][j];
	}
    }
    return sum;
}

```
That gives the compiler more information to work with.
(But it may still fail to prefetch between array rows.)

---

### Post by dribeas on 2009-07-28
> **stroyan said:**
> Another point that could help prefetching is the use of c89 style variable size arrays.
gcc will allow you to use array parameters that have their size defined by other passed parameters, like this-


Note that the compiler will assume what you tell it in the function definition, and will not check that the passed in array is indeed the given size. The compiler will use the information to work out the offsets inside the function but will use the array argument as a pointer to the same element. (In C and C++ arrays decay into pointers when passed as function arguments).

So... you must be careful when using such functions as the compiler will not do type checking for array sizes.

---

### Post by stroyan on 2009-07-28
> **dribeas said:**
> Note that the compiler will assume what you tell it in the function definition, and will not check that the passed in array is indeed the given size. The compiler will use the information to work out the offsets inside the function but will use the array argument as a pointer to the same element. (In C and C++ arrays decay into pointers when passed as function arguments).

So... you must be careful when using such functions as the compiler will not do type checking for array sizes.

I think you misunderstand.
The variable size format I showed actually produces code that uses the array dimensions from the integer parameters that are passed in.
The size of the array is not known from the function definition alone.
One function can handle various sizes of array.
It is true that you can call the function with incorrect parameters and get undefined behavior.

---

### Post by dribeas on 2009-07-29
> **stroyan said:**
> I think you misunderstand.
The variable size format I showed actually produces code that uses the array dimensions from the integer parameters that are passed in.
The size of the array is not known from the function definition alone.
One function can handle various sizes of array.
It is true that you can call the function with incorrect parameters and get undefined behavior.

What I meant can be shown in this code snippet:
```

void f( int rows, int cols, int array[rows][cols] );
int main() {
   int array[3][3];
   f( 3, 3, array ); // correct and expected
   f( 2, 4, array ); // compiles just fine there is no type check, still safe
   f( 4, 4, array ); // compiles fine, but will probably produce a buffer overrun
}

```

The compiler will allow all three calls, and it is the programmer responsibility writing the correct call. The compiler will not help you if you enter incorrect sizes.

As compared to (C++ with array type check):

```

template <std::size_t rows, std::size_t cols>
void f( int (&array)[rows][cols] );

int main()
{
   int array[3][3];
   f( array ); // compiler will deduce 'rows' and 'cols' to 3, 3
}

```

In the C++ example, the compiler can work out the dimensions and the call is type safe: dimensions are known by the compiler. The problem in the C++ solution is that the executable (or lib) size will grow in size, as the template will be instantiated for each different combinations of sizes.

---

