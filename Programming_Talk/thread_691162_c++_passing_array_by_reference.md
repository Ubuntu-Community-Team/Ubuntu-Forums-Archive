---
title: "c++ passing array by reference"
date: 2008-02-08
forum: Programming Talk
---

### Post by nbo10 on 2008-02-08
Hi All,
I'm having a major brain lapse on trying to figure this out and googling is just confusing me more. I have some large arrays that I'm taking slices from. I wrote a simple program to test my method of passing/returning arrays from a function. I'm missing something and friday morning isn't helping me. The problem I think is assigning the values to the second array. 

 

```

void Take_Slice(double* Array, double* Slice);


void Take_Slice(double* Array, double* Slice)
{
	cout << *Array <<endl;
	cout << *(Array+1) <<endl;
	*Slice = *Array;
	*Slice+1 = *Array+4;
	*Slice+2 = *Array+6;		
;
}

int main()
{
	double A[10]={0.1,1.4,2,3,4,5,6,7,8,9};
	double B[3];
	Take_Slice(A,B);
cout << B[0] << "\t" << B[1] << "\t" <<B[2] <<endl;

cout << "Ehllo";
return 0;
```

---

### Post by RJ8722 on 2008-02-08
I kind of re-wrote it for you and this seems to work.

```

#include <iostream>
using namespace std;

void Take_Slice(double* Array, double* Slice);

void Take_Slice(double* Array, double* Slice)
{
	cout << *Array <<endl;
	cout << *(Array+1) <<endl;
	*Slice = *Array;
	*(Slice+1) = *(Array+4);
	*(Slice+2) = *(Array+6);		
}

int main()
{
	double A[10]={0.1,1.4,2,3,4,5,6,7,8,9};
	double B[3];
	Take_Slice(A,B);
	cout << B[0] << "\t" << B[1] << "\t" <<B[2] <<endl;

	cout << "Ehllo";
	return 0;
}

```

You were just missing some ( ) around Array+4 and Array+6 and stuff like that.

---

### Post by nbo10 on 2008-02-08
That does it thanks.

---

### Post by hod139 on 2008-02-08
If this is C++ why are you using C-style arrays instead of vectors?

---

### Post by nbo10 on 2008-02-08
Doh.... I forgot that Array is going to be a three dimensional array, Array[][][].

---

### Post by hod139 on 2008-02-08
> **nbo10 said:**
> Doh.... I forgot that Array is going to be a three dimensional array, Array[][][].
Why do you need a 3-dimensional array?  You still can use vectors if you really do need a 3 dimensional array:
```

std::vector< std::vector< std::vector<T> > > threeDimVec;

```
So, again, why are you using C-style arrays in C++?

---

### Post by revanthedarth on 2008-02-08
Vectors aren't fast as pure-c arrays. And there is no need to use the complex solution if simple one helps (KISS rule).

I'd recommend a struct-class containing type-pointer-pointer-pointer (type***). C++ is pain in the *** when passing multi-dimensional arrays to functions. func(type**** a) helps, but you can't pass type arr[10][12][8]. Use classes, much more easier (to code and read) than vector-based solution.

I know that C++ is good, and so is STL. But STL isn't supposed to contain the only (or best) data structure or container. For example, i use my own linked list, but i don't bother coding a heap, pq helps :)

And know that, you can't find a better data structure or container than the ones you coded. But it doesn't mean that they are the fastest :)

---

### Post by aks44 on 2008-02-08
> **revanthedarth said:**
> Vectors aren't fast as pure-c arrays.
Prove it?

---

### Post by CptPicard on 2008-02-09
> **revanthedarth said:**
> Vectors aren't fast as pure-c arrays. And there is no need to use the complex solution if simple one helps (KISS rule).

Yes they are. I haven't looked at the compiler output but I'd bet quite a lot that it essentially compiles into the same thing as a c-array. And there is no reason to use the more bug-prone raw array solution if you've got the STL version which most importantly helps you with memory management issues.

> 
I know that C++ is good, and so is STL. But STL isn't supposed to contain the only (or best) data structure or container.

Yes it is. It's supposed to contain implementations that are tried and tested and thoroughly debugged and optimized, so that you don't have to roll your own. Unless  you're a total programming god, you won't be able to beat with an ad hoc solution what you get from a good library.

> For example, i use my own linked list, but i don't bother coding a heap, pq helps :)

Why would you do that? I can't imagine bothering debugging my own versions of simple structures, unless I'm coding something much more custom than just a linked list...

> And know that, you can't find a better data structure or container than the ones you coded.

Which would pretty much disprove the need for STL in the first place, as everyone would be better off rolling their own. :)

---

### Post by mike_g on 2008-02-09
I thought vectors did bounds checking to make sure you don't read/write out of buffer. I might be wrong here,  but if not then that would make it slower.

---

### Post by aks44 on 2008-02-09
> **CptPicard said:**
> Yes they are. I haven't looked at the compiler output but I'd bet quite a lot that it essentially compiles into the same thing as a c-array.

You're perfectly right. Like most of the STL, vector code is inlined by the compiler and optimized away.


> **mike_g said:**
> I thought vectors did bounds checking to make sure you don't read/write out of buffer. I might be wrong here,  but if not then that would make it slower.
Vectors *can* do bounds checking (which obviously make the code slower), but it's an optional feature.




While we're on that topic (C arrays vs C++ vectors), can anyone fill-in the following C function please?
```
void increment_array(int* array, unsigned size)
{
  // TODO: increment each array element by one
}
```

---

### Post by CptPicard on 2008-02-09
Is this a test? :p

Well then, let's see what I'm doing wrong...

```

for (int i = 0; i < size; i++)
  (*(array+i))++;

```

EDIT: Ok, ok... I like my pointer arithmetic too much... array[i]++ then. :)

---

### Post by aks44 on 2008-02-09
Is this kind of code idiomatic to C?

EDIT: CptPicard I just saw your own edit, but I guess we'll agree that this is only a minor syntax change. The generated code would be the same.

---

### Post by CptPicard on 2008-02-09
... yes?

---

### Post by aks44 on 2008-02-09
Thanks, you just made my point. ;)


Here's the *_idiomatic_* C++ way of doing it:

```
void increment_array(std::vector<int>& vect)
{
  for (std::vector<int>::iterator i = vect.begin(); i != vect.end; ++i)
    ++(*i);
}
```


The STL's design (and many other C++'ish libraries like eg. boost) actively promotes the use of iterators rather than indices. Why? Because iterators work the same way on vectors, lists, or any other data structures (EDIT: *as far as sequential access goes*, see discussion below), while indices require random-access containers. I'll spell it: orthogonality. :)

Here's the above code, translated to equivalent C code:

```
void increment_array(int* array, unsigned size)
{
  int* end_array = array + size;
  for (int* i = array; i != end_array; ++i)
    ++(*i);
}
```

As a side effect (it's not the primary intent), using iterators is almost always more efficient than using indices (if using indices is even possible), there are a few corner cases where both are equivalent though.

My whole point being: C++ vector-based code will quite often be more efficient than using C arrays, not because of each language's technical merits but because of the associated idioms.

Writing such efficient code in C requires some thinking, in C++ this is the normal way to do it.

Back to mike_g's remark about bounds checking: unless you really need *random* access to the container (which is quite seldom), then you don't even need to bother about array bounds. Getting it wrong with iterators really require serious screw-up skills... ;)

So there. :p

---

### Post by mike_g on 2008-02-09
> Is this a test?

Well then, let's see what I'm doing wrong...

Code:

for (int i = 0; i < size; i++)
  (*(array+i))++;

Well since this is a C test you are declaring an int inside a for loop. Thats wrong :p Nice obfuscation tho ;)

> Back to mike_g's remark about bounds checking: unless you really need *random* access to the container (which is quite seldom), then you don't even need to bother about array bounds. Getting it wrong with iterators really require serious screw-up skills..
Well I have had times where I found it very easy to accidentally write out of bounds without using random access. For example: drawing shapes and stuff to an image buffer.

I learnt C first so kind of stuck with C style coding, but since everyone seems to like std::vector so much I guess I'll have to have a play around with them :)

---

### Post by hod139 on 2008-02-09
> **aks44 said:**
>  Because iterators work the same way on vectors, lists, or any other data structures, while indices require random-access containers. I'll spell it: orthogonality.
I hate to do this because you probably already know this, but your statement is not correct.  Iterators do not work the same on vectors, lists, or any other data structures.  With vectors you have random access iterators, whereas with lists say, you have bidirectional iterators.  A random access iterator extends the bidirectional iterator adding pointer arithmetic, and iterator subtraction. All the details of different iterator types can be found at SGI's website: [http://www.sgi.com/tech/stl/Iterators.html](http://www.sgi.com/tech/stl/Iterators.html)

---

### Post by hod139 on 2008-02-09
> **mike_g said:**
> Well since this is a C test you are declaring an int inside a for loop. Thats wrong :p Nice obfuscation tho ;)

It isn't wrong, it's been valid C since the 1999 standard was released.  gcc defaults to the older ISO C90 plus gnu extensions standard, to use the newer C99 ISO standard type
```
 gcc -std=c99

```

---

### Post by mike_g on 2008-02-09
Oops. My bad then. Guess I'll have to compile with gcc using C99 standard. Thanks for the tip.

---

### Post by aks44 on 2008-02-09
> **hod139 said:**
> I hate to do this because you probably already know this, but your statement is not correct.

Good point. ;) What I had in mind was "*iterators work the same way on any data structure _as far as sequential access goes_*" but as you pointed it out, my post doesn't reflect that... :oops:


EDIT: yeah, I know... slist doesn't have bidi iterators, so much for "sequential access" in the generic sense... ;)

---

### Post by CptPicard on 2008-02-09
Aks, it is a good point you're making... using the iterator abstraction from the get-go allows compiler to optimize away one addition per iteration, while in C one really needs to more explicitly code for it.

And mike, no, I was not intentionally obfuscating anything :) I do very rarely use the index notation in my C.

If one really wants to tighten this up close to obfuscation and to follow aks's iterator remarks... :p

```

while (size-- > 0)
  (*(array++))++;

```

---

### Post by hod139 on 2008-02-09
> **aks44 said:**
> 
EDIT: yeah, I know... slist doesn't have bidi iterators, so much for "sequential access" in the generic sense... ;)
Beat me to it :)


And while I'm nitpicking...
> **CptPicard said:**
> 
```

while (size-- > 0)
  (*(array++))++;

```

Shouldn't that be ```
  ++(*(array++)); 
```
to avoid creating a temporary when incrementing (though the compile will probably do this for you :))

---

### Post by aks44 on 2008-02-09
> **CptPicard said:**
> Aks, it is a good point you're making... using the iterator abstraction from the get-go allows compiler to optimize away one addition per iteration, while in C one really needs to more explicitly code for it.
Now you understand why I didn't explain it *before* anyone posted some code... I needed an un-hinted answer ;)




**EDIT: my bad, the error I mention below was my only fault... please disregard the rest of this post** (see my next post for explanation) :oops:

> **CptPicard said:**
> ```
while (size-- > 0)
  (*(array++))++;

```

> **hod139 said:**
> And while I'm nitpicking... Shouldn't that be ```
  ++(*(array++)); 
```


Guys, I don't mean to be a pain, but... ;)
```
$ gcc -o test test.c -std=c99
test.c: In function «main":
test.c:17: erreur: invalid lvalue in increment
```

(line 17 is the (*(array++))++ line, both of your versions yield the same result)

I was having trouble deciding what that line did *exactly* (in which order, more precisely) so I decided to compile it...

---

### Post by hod139 on 2008-02-09
I actually did test my code before posting, here is my entire app (note, this was a quick hack):

```

#include <stdio.h>
void inc(int* array, int size)
{
  while (size-- > 0)
    ++(*(array++));
}

int main()
{
  int array[] = {0,1,2,3,4};
  inc(array, 5);
 
  int size = 5;
  int *i = &array[0];
  while (size-- > 0)
    printf( "%d, " ,(*(i++)));
  printf("\n");
  return 0;
}


```Compiles using
```
 gcc -std=c99 test.c 
```
or just  ```
 gcc test.c 
``` (the older standard works too)

---

### Post by pmasiar on 2008-02-09
Call to C++ experts: this is interesting discussion, we could have some thread collecting link to such threads. It went off-topic, but in an interesting way. All it needs short summary of what more generic problen suggested by original post was discussed after post #X. That summary can be used as "teaser" for a link from higher level FAQ about C++.

---

### Post by aks44 on 2008-02-09
Ok, this was my fault, I didn't pay attention... :oops:

Here is the code I was trying to compile (shame on me for not spotting it earlier, that really shows that I'm definitely not used to C idioms, especially when it comes to arrays ;)):

```
#include <stdio.h>

#define SIZE 5

int main()
{
  int array[SIZE];
  for (int i=0; i<SIZE; ++i)
  {
    array[i] = i;
    printf("%d ",i);
  };
  printf("\n");

  unsigned size = SIZE;
  while (size-- > 0)
    ++(*(array++));

  for (int i=0; i<SIZE; ++i)
    printf("%d ",array[i]);
  printf("\n");
}
```


Changing the loop part to the following code solved it:
```
  unsigned size = SIZE;
  int* arr = array;
  while (size-- > 0)
    ++(*(arr++));
```


And yeah, I know I'm using the very same indexed loops I was "criticizing" earlier... ;)

---

### Post by hod139 on 2008-02-09
> **aks44 said:**
> 
I was having trouble deciding what that line did *exactly* (in which order, more precisely) so I decided to compile it...
In case others are/were having the same trouble:
```

++(*(array++));
```This first post-increments the array pointer (which returns the current location, not the location after the increment), then dereferences the array at the returned pointer location, then pre-increments the dereferenced value.  At the end, array now points to the next element, and the value at the current location was incremented.


Your later post  brings up something interesting:
> **aks44 said:**
> 

```
#include <stdio.h>

#define SIZE 5

int main()
{
  int array[SIZE];
  <snip>

  unsigned size = SIZE;
  while (size-- > 0)
    ++(*(array++));

  <snip>
}
```

The reason this was giving you a compile error was because you allocated the array on the stack, which makes the array pointer constant.  That's why the array++ line caused a compile error.  However, if you allocated the array on the heap, some very bad things will happen if you start playing with the array pointer.

```

int main()
{
  int *array = malloc(SIZE*sizeof(int));
  ++array;  // bad, but legal

  free(array); // BOOM
  return 0;
}

``` We can increment the array pointer now because the pointer is not constant, but very bad things can (and will) happen.  The free will cause a fault, since the pointer does not point to the start of the allocated memory, and malloc really hates that :) !

---

### Post by aks44 on 2008-02-09
> **hod139 said:**
> The reason this was giving you a compile error was because you allocated the array on the stack, which makes the array pointer constant.  That's why the array++ line caused a compile error.

Yup, I realized that after compiling your code and comparing it to mine.

I never actually use C arrays, and TBH I got caught by the classic "arrays decay to pointers" ambiguous half-truth... ;)

---

### Post by stroyan on 2008-02-09
There are a lot of opinions about performance being stated here and no measurements.
Here is an actual small benchmark that shows an array style can be much faster than a vector style.
That is particularly important for three dimensional arrays when comparing an array of know sizes to vectors of vectors or pointers to arrays of pointers.
Excessive indirection is really hard on modern CPUs.
This simple benchmark does array increment in many different styles.
I compiled and ran this on a core 2 duo with 32 bit g++ 4.1.3.
[IMG]http://stroyan.net/arrays.png[/IMG]

```
$ g++ -O -o arrays arrays.cpp
$ ./arrays
679111 increment_vector()'s per second
218624 increment_vector_index()'s per second
739921 increment_array()'s per second
735581 increment_array_index()'s per second
340756 increment_3D_vector()'s per second
104754 increment_3D_vector_index()'s per second
500944 increment_3Dp_array()'s per second
127301 increment_3Dp_array_index()'s per second
738034 increment_3D_array()'s per second
473999 increment_3D_array_index()'s per second
$ g++ -O -funroll-loops -o arrays_unrolled arrays.cpp
$ ./arrays_unrolled
664915 increment_vector()'s per second
219851 increment_vector_index()'s per second
1236389 increment_array()'s per second
1238488 increment_array_index()'s per second
341008 increment_3D_vector()'s per second
104946 increment_3D_vector_index()'s per second
720258 increment_3Dp_array()'s per second
170946 increment_3Dp_array_index()'s per second
1277972 increment_3D_array()'s per second
1341380 increment_3D_array_index()'s per second
$ 
```

```
#include <stdio.h>
#include <time.h>
#include <sys/types.h>
#include <sys/param.h>
#include <sys/time.h>
#include <errno.h>
#include <stdlib.h>
#include <unistd.h>
#include <malloc.h>

#include <vector>

#ifndef LOOPS
#define LOOPS 1000000
#endif

#define BENCH(function,message) \
{ \
        register int i; \
        struct timeval time1, time2; \
        struct timezone tz; \
        double elapsed_time; \
\
        gettimeofday(&time1, &tz); \
        for (i=0; i<LOOPS; i++) { \
                function; \
        } \
        gettimeofday(&time2, &tz); \
        elapsed_time = time2.tv_sec - time1.tv_sec \
                + (time2.tv_usec - time1.tv_usec) / 1e6; \
        printf("%.0f %s\n", LOOPS / elapsed_time, message); \
}


void increment_vector(std::vector<int>& vect)
{
    for (std::vector<int>::iterator i = vect.begin(); i != vect.end(); ++i)
        ++(*i);
}

void increment_vector_index(std::vector<int>& vect)
{
    for (int i=0; i<vect.size(); i++)
        vect[i]+=1;
}

void increment_3D_vector(std::vector< std::vector< std::vector<int> > >& vect)
{
    std::vector< std::vector< std::vector<int> > >::iterator i;
    std::vector< std::vector<int> >::iterator j;
    std::vector<int>::iterator k;
    for (i = vect.begin(); i != vect.end(); ++i)
        for (j = (*i).begin(); j != (*i).end(); ++j)
            for (k = (*j).begin(); k != (*j).end(); ++k)
                ++(*k);
}

void increment_3D_vector_index(std::vector< std::vector< std::vector<int> > >& vect)
{
    for (int i=0; i<vect.size(); i++)
        for (int j=0; j<vect[i].size(); j++)
            for (int k=0; k<vect[i].size(); k++)
                vect[i][j][k]+=1;
}

void increment_array(int A[], int size)
{
    int *p = &A[0];
    int *end = &A[size];
    while (p<end)
        *(p++)+=1;
}

void increment_array_index(int A[], int size)
{
    for (int i=0; i<size; i++)
        A[i]+=1;
}

void increment_3Dp_array(int ***A, int size1, int size2, int size3)
{
    int ***p1 = A;
    int ***end1 = p1+size1;
    while (p1<end1)
    {
        int **p2 = *p1;
        int **end2 = p2+size2;
        while (p2<end2)
        {
            int *p3 = *p2;
            int *end3 = p3+size3;
            while (p3<end3)
                *(p3++)+=1;
            p2+=1;
        }
        p1+=1;
    }
}

void increment_3Dp_array_index(int ***A, int size1, int size2, int size3)
{
    for (int i=0; i<size1; i++)
        for (int j=0; j<size2; j++)
            for (int k=0; k<size3; k++)
                A[i][j][k]+=1;
}

void increment_3D_array(int A[10][10][10])
{
    int *p = &A[0][0][0];
    int *end = &A[9][9][9];
    while (p<=end) (*p++)++;
}

void increment_3D_array_index(int A[10][10][10])
{
    for (int i=0; i<10; i++)
        for (int j=0; j<10; j++)
            for (int k=0; k<10; k++)
                A[i][j][k]+=1;
}

int main(int argc, char *argv[])
{
    std::vector<int> V;
    V.resize(1000);
    BENCH(increment_vector(V), "increment_vector()'s per second")

    BENCH(increment_vector_index(V), "increment_vector_index()'s per second")

    int A[1000];
    for (int i=0; i<1000; i++) A[i]=0;
    BENCH(increment_array(A, 1000), "increment_array()'s per second")

    for (int i=0; i<1000; i++) A[i]=0;
    BENCH(increment_array_index(A, 1000), "increment_array_index()'s per second")

    std::vector< std::vector< std::vector<int> > > V3;
    V3.resize(10);
    for (int i=0; i<10; i++)
    {
        V3[i].resize(10);
        for (int j=0; j<10; j++)
            V3[i][j].resize(10);
    }
    BENCH(increment_3D_vector(V3), "increment_3D_vector()'s per second")
    BENCH(increment_3D_vector_index(V3), "increment_3D_vector_index()'s per second")

    int **A3p[10];
    for (int i=0; i<10; i++) {
        A3p[i] = (int **) malloc(10*sizeof(int *));
        for (int j=0; j<10; j++) {
            A3p[i][j] = (int *) calloc(10 , sizeof(int));
        }
    }
    BENCH(increment_3Dp_array(A3p,10,10,10), "increment_3Dp_array()'s per second")
    BENCH(increment_3Dp_array_index(A3p,10,10,10), "increment_3Dp_array_index()'s per second")

    int A3[10][10][10];
    for (int i=0; i<10; i++)
        for (int j=0; j<10; j++)
            for (int k=0; k<10; k++)
                A3[i][j][k]=0;
    BENCH(increment_3D_array(A3), "increment_3D_array()'s per second")
    BENCH(increment_3D_array_index(A3), "increment_3D_array_index()'s per second")

    return 0;
}
```

---

### Post by Jessehk on 2008-02-09
Getting back to the original topic, Boost.MultiArray is nice for multi-dimensional arrays.

[http://boost.org/libs/multi_array/doc/index.html](http://boost.org/libs/multi_array/doc/index.html)

```

#include <boost/multi_array.hpp>

// Grid is a two-dimensional array of ints. You specify dimensions
// when you initialize the array.
typedef boost::multi_array<int, 2> Grid;

```

---

### Post by hod139 on 2008-02-10
> **stroyan said:**
> There are a lot of opinions about performance being stated here and no measurements.
Here is an actual small benchmark that shows an array style can be much faster than a vector style.

I don't believe your results, and to prove your benchmarks wrong I am going to use the timing code that was used to time the STL sort functions (written by Professor Musser and available [here]("http://www.cs.rpi.edu/%7Emusser/stl-book/source/timer.h")).

In your benchmark, you disabled optimizations, which is super unfair.  Without optimizations the compiler is not allowed to use fancy template tricks, or do any inlining, or whatever else it does.  Also, the time function is very unreliable at such small run times.  My solution (really, Musser's) counts the number of iterations of the function, which is far more accurate.  For my results, I only compared the pointer methods, not the indexing. 


Now the results.  First, your increment_vector function versus your  increment_array:
```

sberard@sberard-laptop:~/temp$ g++ -Wall -O2 timing.cpp
sberard@sberard-laptop:~/temp$ ./a.out
Repetitions, initial size, and final size: 5 4 2048
Timing increment_vector
Baseline time: 0.00456456
                                  4     -0.0001 ms
Baseline time: 0.0045
                                  8     -0.0000 ms   0.5631
Baseline time: 0.0045
                                 16      0.0000 ms  -0.1354
Baseline time: 0.0045
                                 32      0.0000 ms   5.2681
Baseline time: 0.0046
                                 64      0.0002 ms   6.3904
Baseline time: 0.0047
                                128      0.0001 ms   0.5585
Baseline time: 0.0051
                                256      0.0003 ms   3.1946
Baseline time: 0.0048
                                512      0.0008 ms   2.8716
Baseline time: 0.0065
                               1024      0.0014 ms   1.7189
Baseline time: 0.0084
                               2048      0.0028 ms   1.9932
Timing increment_array
Baseline time: 0.0045
                                  4     -0.0000 ms
Baseline time: 0.0045
                                  8      0.0000 ms  -0.0288
Baseline time: 0.0045
                                 16      0.0000 ms  41.2680
Baseline time: 0.0045
                                 32      0.0000 ms   1.8433
Baseline time: 0.0045
                                 64      0.0003 ms  41.0626
Baseline time: 0.0048
                                128      0.0000 ms   0.1619
Baseline time: 0.0050
                                256      0.0003 ms   7.1727
Baseline time: 0.0054
                                512      0.0008 ms   2.7557
Baseline time: 0.0065
                               1024      0.0013 ms   1.5561
Baseline time: 0.0084
                               2048      0.0026 ms   2.0257

```The first line ```
Repetitions, initial size, and final size: 5 4 2048
```indicates that for each size of the vector, I time the increment function 5 times (reporting the median time).  The vector size starts at 4 and increase to 2048, doubling each iteration.

The first column (baseline) is the time it took to restore the array during the 5 runs (and was removed from the final timing).  The second column indicates the size of the vector.  The third column is the time it took.  The final column is the growth rate of the time.

As you can clearly see, the runs times are pretty much identical.  Also, for the CS inclined, you can see that as we increase the problem size the function begins to experience a linear growth (doubling the problem size results in a doubling of the time), which is expected for these functions.


Now, onto the 3D arrays:
```

sberard@sberard-laptop:~/temp$ g++ -Wall -O2 timing3D.cpp
sberard@sberard-laptop:~/temp$ ./a.out
Repetitions, initial size, and final size: 5 4 128
Timing increment_3D_vector
Baseline time: 0.00653582
                                  4     -0.0009 ms
Baseline time: 0.0082
                                  8      0.0009 ms  -0.9445
Baseline time: 0.0237
                                 16      0.0073 ms   8.4468
Baseline time: 0.1120
                                 32      0.0568 ms   7.7485
Baseline time: 0.9363
                                 64      0.4902 ms   8.6375
Baseline time: 12.8205
                                128     10.4353 ms  21.2877
increment_3Dp_array
Baseline time: 0.0051
                                  4      0.0003 ms
Baseline time: 0.0093
                                  8      0.0011 ms   4.1221
Baseline time: 0.0431
                                 16      0.0088 ms   8.2370
Baseline time: 0.3109
                                 32      0.0634 ms   7.2438
Baseline time: 2.7701
                                 64      1.0613 ms  16.7281
Baseline time: 22.7273
                                128     12.9870 ms  12.2365

```I set the 3d arrays to have size n*n*n, so when you see the size displayed, the actual size is n^3.  These sizes grew a lot faster, so I had to stop earlier. Again, the vectors are just as fast. Also, for the CS inclined, we would expect the times to grow by a factor of 8 as we double the size, since the algorithm is now n^3 (I'm not sure why we don't see that with the last result.  Maybe the optimizations messed up the time, or maybe my laptop was starting to overheat :) )


So, I have now debunked your benchmark, and shown with actual numbers that there is no real speed difference between STL's vector and C's array.  And the code for using STL's vector is much cleaner/safer.  I have attached my benchmark code and [timer.h]("http://www.cs.rpi.edu/%7Emusser/stl-book/source/timer.h"). (I had to add a .txt extension, it wouldn't let me upload .cpp or .h files.)

---

### Post by mb108 on 2008-02-10
This discussion is awesome. :popcorn:

---

### Post by aks44 on 2008-02-10
> **stroyan said:**
> There are a lot of opinions about performance being stated here and no measurements.
FWIW there was no need to measure anything, these are not opinions but technical facts. Anyone that has a good understanding of the compilation process realizes that.


> **stroyan said:**
> Here is an actual small benchmark that shows an array style can be much faster than a vector style.
As hod139 pointed it out, your "benchmark" only shows that meaningful benchmarks are quite hard to put together. ;)

---

### Post by stroyan on 2008-02-11
> **hod139 said:**
> 
In your benchmark, you disabled optimizations, which is super unfair.  Without optimizations the compiler is not allowed to use fancy template tricks, or do any inlining, or whatever else it does.

I did use '-O -funroll-loops' optimization.  But you are right that -O2 helps the vector code a lot.  Thank you for pointing that out.
I spent too many years using a compiler that mapped '-O' to '-O2'.
g++ caught me off guard with it mapping to '-O1'.
The '-O2' setting does not not include '-funroll-loops', which is also helpful.
> **hod139 said:**
> 
Also, the time function is very unreliable at such small run times.  My solution (really, Musser's) counts the number of iterations of the function, which is far more accurate.  For my results, I only compared the pointer methods, not the indexing. 
My benchmark uses getitimeofday() rather than time() as yours does.
The gettimeofday() function returns microseconds, making it up to 1 million times more precise than time().
The timer that you used uses the less precise time() function and compensates for that by calling it thousands of times watching for when the second value changes.
The slower a timed function is the less accurate that becomes because you don't know how long ago the second value changed before you called check().
> **hod139 said:**
> 
I set the 3d arrays to have size n*n*n, so when you see the size displayed, the actual size is n^3.  These sizes grew a lot faster, so I had to stop earlier. Again, the vectors are just as fast. Also, for the CS inclined, we would expect the times to grow by a factor of 8 as we double the size, since the algorithm is now n^3 (I'm not sure why we don't see that with the last result.  Maybe the optimizations messed up the time, or maybe my laptop was starting to overheat :) ) 

The larger 3D arrays would exceed the size of cache.  That will slow the memory access time and change the factor of 8 ratio.
(The increment_3Dp_array case seems to hit that cache limit sooner because of the way you interleaved allocation of the 'a' and 'a0' arrays.  That could make 'a' reside on more cache lines.)

---

### Post by hod139 on 2008-02-11
> **stroyan said:**
> 
My benchmark uses getitimeofday() rather than time() as yours does.
The gettimeofday() function returns microseconds, making it up to 1 million times more precise than time().

Don't get fooled into thinking that gettimeofday is any more accurate.  From the reference page:
> 
 **_int gettimeofday(timeval *tp, NULL)_**
      *include: <sys/time.h>*
      **Note** In C programs (as opposed to C++) the word "struct" must appear before "timeval". Gets the time of day. The parameter must be a pointer to a previously declared timeval variable (or in C, a struct timeval variable). This struct type is also defined in <sys/time.h>. A timeval has two components, both ints. One (called tv_sec) is exactly the value that would be returned by [time]("http://rabbit.eng.miami.edu/info/functions/time.html#time"), the time in seconds since 1/1/1970. The other (called tv_usec) is the number of microseconds into that second. **Don't be fooled: although the units are microseconds, the value is nothing like that accurate. On many systems, 10000 is added 100 times per second.**
(emphasis added)

> 
The timer that you used uses the less precise time() function and compensates for that by calling it thousands of times watching for when the second value changes.
The slower a timed function is the less accurate that becomes because you don't know how long ago the second value changed before you called check().
This is a very good point, and one I think should be emphasized.  The compensation trick used by Musser for the low granularity of the time function will cause problems when the timed functions start to take longer (as you said).  Ideally, a test time of the algorithm should be performed and if above some magic number, normal timing (i.e. your solution) should be done.  If below some magic number, then Musser's technique should be used.

> 
The larger 3D arrays would exceed the size of cache.  That will slow the memory access time and change the factor of 8 ratio.
(The increment_3Dp_array case seems to hit that cache limit sooner because of the way you interleaved allocation of the 'a' and 'a0' arrays.  That could make 'a' reside on more cache lines.)

I didn't think about cache issues, this could very well be the cause.

---

### Post by nbo10 on 2008-02-11
So, I don't really understand most of this thread. But I used arrays because thats what I knew how to do and I needed the answers fast.  If someone could enlighten me on how to use vectors I would thankful.

The workhouse of my code is.
field[][][] is a complex double.
```
for(h = -3;h<=3;h++){
	for(k=-3;k<=3;k++){
		m++;
		cout << m << endl;
		for(int xi=0;xi<gridsize;xi++){
			for(int yi=0;yi<gridsize;yi++){
				complex<double> num(0, q* (h*(xi*dx - 300 ) + k*(yi*dy - 300)));
			//	Field[xi][yi][0] = Field[xi][yi][0] +  FormFactor[h+3][k] * exp(num);
				Field[xi][yi][m-1] = FormFactorAveTotal[h+3][k+3] *   exp(num);
			//	cout << exp(num) << endl;
				//cout << yi*dy - (ysize)*a/2 <<endl;
				//postion[xi][yi] = xsize
	//			cout << h <<" " << k << endl; 
			}
		}
	}
}
```

 I then compare the different field[][][i] values for different parameters.

Thanks

---

### Post by hod139 on 2008-02-11
For example, you would change your array declarations to be:
```

  std::vector< std::vector< std::vector<double> > > Field;
  std::vector< std::vector<double> > FormFactorAveTotal;

```And then you never have to do new or delete on the vector.  If you want to resize the vectors, you use the .resize() member function.
```

  std::vector< std::vector< std::vector<double> > > Field;
  Field.resize(gridsize);
  std::vector< std::vector< std::vector<double> > >::iterator itr1 = Field.begin();
  for( ; itr1 != Field.end(); ++itr1){
     itr1->resize(gridsize);
     std::vector< std::vector<double> >::iterator itr2 = itr1->begin();
     for( ; itr2 != itr1->end(); ++itr2){
       itr2->resize(3);
     }
  }

```

For index referencing of the vectors, nothing would change, however, I would suggest you use iterators (as shown above and explained in previous posts) when you can.

---

### Post by nbo10 on 2008-02-11
> **hod139 said:**
> For example, you would change your array declarations to be:
```

  std::vector< std::vector< std::vector<double> > > Field;
  std::vector< std::vector<double> > FormFactorAveTotal;

```And then you never have to do new or delete on the vector.  If you want to resize the vectors, you use the .resize() member function.
```

  std::vector< std::vector< std::vector<double> > > Field;
  Field.resize(gridsize);
  std::vector< std::vector< std::vector<double> > >::iterator itr1 = Field.begin();
  for( ; itr1 != Field.end(); ++itr1){
     itr1->resize(gridsize);
     std::vector< std::vector<double> >::iterator itr2 = itr1->begin();
     for( ; itr2 != itr1->end(); ++itr2){
       itr2->resize(3);
     }
  }

```

For index referencing of the vectors, nothing would change, however, I would suggest you use iterators (as shown above and explained in previous posts) when you can.

I use programming for practical purpose's. And I don't understand what that code is doing. I'll stick to what I know.

---

### Post by LaRoza on 2008-02-11
> **nbo10 said:**
> I use programming for practical purpose's. And I don't understand what that code is doing. I'll stick to what I know.

That is doing the same thing you posted earlier.

---

### Post by stroyan on 2008-02-11
> **hod139 said:**
> Don't get fooled into thinking that gettimeofday is any more accurate.  From the reference page:
(emphasis added)
...
**Don't be fooled: although the units are microseconds, the value is nothing like that accurate. On many systems, 10000 is added 100 times per second.**

I don't know which reference you are looking at.  The ubuntu "man gettimeofday" does not say that.
The only place google found that phrase was at [http://rabbit.eng.miami.edu/info/functions/time.html](http://rabbit.eng.miami.edu/info/functions/time.html) .
The truth is that ubuntu and other linux distributions have a very accurate gettimeofday.
You can verify the small difference between measurements with a simple program.
If you want a function that assures you of the effective resolution you can link with -lrt and use the clock_gettime and clock_getres functions as show below.
```
$ cat clock_resolution.c
#include <stdio.h>
#include <time.h>
#include <sys/time.h>

int main(int argc, char *argv[])
{
        struct timeval t1, t2;
        struct timezone timez;
        struct timespec tp1, tp2, res;
        double elapsed_time, resolution;

        gettimeofday(&t1, &timez);
        do {
            gettimeofday(&t2, &timez);
            elapsed_time = t2.tv_sec - t1.tv_sec
                + (t2.tv_usec - t1.tv_usec) / 1e6;
        } while (elapsed_time == 0.0);
        printf("gettimeofday changed with elapsed time of %lg\n", elapsed_time);

        clock_gettime(CLOCK_REALTIME, &tp1);
        do {
            clock_gettime(CLOCK_REALTIME, &tp2);
            elapsed_time = tp2.tv_sec - tp1.tv_sec
                + (tp2.tv_nsec - tp1.tv_nsec) / 1e9;
        } while (elapsed_time == 0.0);
        printf("clock_gettime changed with elapsed time of %lg\n", elapsed_time);

        clock_getres(CLOCK_REALTIME, &res);
        resolution = tp2.tv_sec - tp1.tv_sec
            + (tp2.tv_nsec - tp1.tv_nsec) / 1e9;
        printf("clock_getres reports resolution of %lg\n", resolution);

        return 0;
}
$ cc -Wall -o clock_resolution clock_resolution.c -lrt
$ ./clock_resolution
gettimeofday changed with elapsed time of 1e-06
clock_gettime changed with elapsed time of 2.73e-07
clock_getres reports resolution of 2.73e-07
$
```

---

### Post by hod139 on 2008-02-11
> **stroyan said:**
> I don't know which reference you are looking at.  The ubuntu "man gettimeofday" does not say that.
The only place google found that phrase was at [http://rabbit.eng.miami.edu/info/functions/time.html](http://rabbit.eng.miami.edu/info/functions/time.html) .
The truth is that ubuntu and other linux distributions have a very accurate gettimeofday.
To be honest, I do not have any hard proof that gettimeofday is less accurate than advertised, I've always just heard that it is. That google result was the first I found when searching for gettimeofday not being accurate.  

In any case, it should be faster than time and your sample code shows that it appears to be giving microsecond accuracy; and in the bigger picture I suppose it isn't really that important and I shouldn't have even bothered mentioning it in the first place :)

---

### Post by aks44 on 2008-02-11
What about RDTSC?

```
__inline__ uint64_t rdtsc() {
  uint32_t lo, hi;
  __asm__ __volatile__ ("rdtsc" : "=a" (lo), "=d" (hi));
  return (uint64_t)hi << 32 | lo;
}

```

(Sorry I won't hack the whole benchmark tonight... tomorrow if noone did it in the meanwhile :p)

---

### Post by stroyan on 2008-02-11
> **aks44 said:**
> What about RDTSC?


RDTSC is unreliable on multiprocessor configurations.
Process migration can move to a different TSC that is no synchronized.
(And there is the small matter of complete architecture dependency.)

gettimeofday and clock_gettime adjust for process CPU migration, (except when they are buggy like in some older x86_64 kernels.)

---

### Post by kaulakis on 2008-05-15
There is a syntactic wrinkle in C++ which allows you to completely avoid array dimension rot when you pass an array to a function.

Check this out - the called function is aware of all the dimensions of its argument.

#include <iostream>
using namespace std;

typedef char tA57[5][7];
#define countof(A) (sizeof(A)/sizeof(A[0]))

void f(tA57(&x))
{
  tA579 a;

  cout << countof(a) << " ";
  cout << countof(a[0]) << endl;
}

tA57 foo;
int main()
{
  f(foo);
  return 0;
}
(Prints "5 7") !! OMG how did I DO that???

The critical element is the parentheses in (&x). With them, the compiler understands that 
the argument x is, exactly, a reference to a tA57. No pointer finagling is required. 

The actual _code_ is the same, the machine address of the array is passed. 
But syntactically the type is preserved rather than degraded to int[][7]. 

Often enough, this is exactly what you want. It comes up a lot when using templates. 
 
For some reason, this technique seems to be litle known. 

-- 
Ed Kaulakis

---

