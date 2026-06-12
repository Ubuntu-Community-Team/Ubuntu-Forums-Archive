---
title: "using pointers to loop through 2D array"
date: 2009-04-08
forum: Programming Talk
---

### Post by Ultra Magnus on 2009-04-08
Hi, I was just wondering if anyone could give me a hand.

I'm writing a bit of code using allot of arrays and I've found that having something of the form

```

for (i = 0 ; i < n ; ++i)
{
    *a++ = *b++
}

```

is quicker than

```

for (i = 0 ; i < n ; ++i)
{
    a[i] = b[i] ;
}

```

This is fine but I am using 2D arrays, I have defined my arrays as follows:

```

    n = 5 ;
    m = 5 ;
    ntm = n*m ;
    a = new int*[n] ;
    a[0] = new int[ntm] ;
    for (i = 1 ; i < n ; ++i) a[i] = a[i-1] + m ;

```

so you can access it like a 1D array by looping on a[0][i]. But I cant seem to get the arrays to copy in the same way as I have above. For instance the following just gives me a massive memory related error

```

    for (i = 0 ; i < ntm ; ++i)
    {
        *(a[0])++ = *(b[0])++ ;
        
    }

```

Doing the following works but I have allot of arrays so doing this for all of them would end up being ridiculously messy:

```

    int *t1, *t2 ;
    t1 = a[0] ;
    t2 = b[0] ;
    for (i = 0 ; i < ntm ; ++i)
    {
        *t2++ = *t1++ ;
        
    }

```

Is there a better way of doing this?

Thanks in advance.

James

---

### Post by skirkpatrick on 2009-04-08
Well, if your arrays are of the same data type and size, just use a memcpy:

```
int a[5][5];
int b[5][5];

memcpy(b, a, sizeof(a));

```

---

### Post by dwhitney67 on 2009-04-08
You did not indicate why you must use C-style arrays, so I propose that if possible, attempt to use C++ style arrays.

If you must use C-style arrays, an effective way to copy them is to use memcpy.  Be careful though not to copy addresses, but the contents at those addresses.

Here's a couple of examples; one that uses the tr1 array, the other that uses the Boost library multi-array:
```

#include <tr1/array>
#include <boost/multi_array.hpp>
#include <cassert>

int main()
{
  // Using tr1
  //
  typedef std::tr1::array<int, 2>    OneDim;
  typedef std::tr1::array<OneDim, 2> TwoDim;

  TwoDim a1, a2;

  a1[0][0] = 10;
  a1[0][1] = 20;
  a1[1][0] = 30;
  a1[1][1] = 40;

  a2 = a1;   // copy the array

  for (int i = 0; i < 2; ++i)
  {
    for (int j = 0; j < 2; ++j)
    {
      assert(a1[i][j] == a2[i][j]);
    }
  }


  // Using Boost
  //
  typedef boost::multi_array<int, 2> Array2D;

  Array2D a3(boost::extents[2][2]);   // 2x2 array
  Array2D a4(boost::extents[2][2]);   // 2x2 array

  a3[0][0] = 10;
  a3[0][1] = 20;
  a3[1][0] = 30;
  a3[1][1] = 40;

  a4 = a3;   // copy the array

  for (int i = 0; i < 2; ++i)
  {
    for (int j = 0; j < 2; ++j)
    {
      assert(a3[i][j] == a4[i][j]);
    }
  }
}

```

---

### Post by Ultra Magnus on 2009-04-08
Hi thanks for the response. I have to use c style arrays because my work has to be compatible with that done by other people, also performance is a major issue as we are trying to get something to work in real-time that requires allot of processing, so I'm trying to optimise as I go along. Memcpy is good but I also have allot of loops doing basic things like adding each item in an array - so something like the following.

```

   int *t1, *t2 ;
    t1 = a[0] ;
    t2 = b[0] ;
    for (i = 0 ; i < ntm ; ++i)
    {
        *t2++ += *t1++ ;
        
    }

```

Basically, if i could do what I have done above but without the two temporary variables that would be brilliant.

Thanks,

James

---

### Post by Habbit on 2009-04-08
If you want to do things more complex than adding items, why not use the STL algorithms/functors? In this example I just try to add the items, but you can use any function you like:

```
#include <algorithm>
#include <functional>

// ...
// a and b are two of your special arrays
// ntm is the total number of elements (rows x cols)

std::transform(a[0], a[0] + ntm, b[0], b[0], std::plus<int>());

// equivalent to " b[0][i] += a[0][i] for each i in [0,ntm); "


```

---

### Post by dwhitney67 on 2009-04-08
> **Ultra Magnus said:**
> ...
```

   int *t1, *t2 ;
    t1 = a[0] ;
    t2 = b[0] ;
    for (i = 0 ; i < ntm ; ++i)
    {
        *t2++ += *t1++ ;
        
    }

```

Basically, if i could do what I have done above but without the two temporary variables that would be brilliant.

Thanks,

James
I do not know if one can do what you want; I would recommend that you initialize your variables as you declare them, and perhaps consider assigning the index to a register, but I really do not think this will speed things up that much.

For example:
```

    const int* ta = a;
    int*       tb = b;

    for (register size_t i = 0 ; i < ntm ; ++i)
    {
      *tb++ += *ta++ ;
    }

```

You could also go as far as to define your own Array class that allows you to access the data as you normally would, plus provide the typical operations that you need.  Something like this:
```

#include <cstring>
#include <cassert>
#include <algorithm>
#include <iostream>
#include <iomanip>


void display(const int& val)
{
  std::cout << std::setw(3) << val << " ";
}


template <typename T>
struct Array
{
  public:
    Array(const size_t size)
      : data(new T[size]),
        size(size)
    {
    }

    T& operator[](const size_t index)
    {
      assert(index < size);
      return data[index];
    }

    void operator=(const Array<T>& other)
    {
      assert(this->size == other.size);

      T* tmpTo    = this->data;
      T* tmpOther = other.data;

      for (register size_t i = 0; i < this->size; ++i)
      {
        *(tmpTo++) = *(tmpOther++);
      }
    }

    friend void operator+=(Array<T>& to, const Array<T>& other)
    {
      T* tmpTo    = to.data;
      T* tmpOther = other.data;

      for (register size_t i = 0; i < to.size; ++i)
      {
        *(tmpTo++) += *(tmpOther++);
      }
    }

    T*     data;
    size_t size;
};


int main()
{
  Array<int> a(5);
  Array<int> b(5);

  // Initialize a
  a[0] = 10;
  a[1] = 20;
  a[2] = 30;
  a[3] = 40;
  a[4] = 50;

  std::cout << "cur a = ";
  std::for_each(a.data, a.data + a.size, display);
  std::cout << std::endl;

  // Copy a to b
  // This only works for simple data types where there is no memory allocated
  // within the data type being copied.  It is not recommended for 'complex'
  // objects.
  memcpy(b.data, a.data, b.size * sizeof(int));

  std::cout << "cur b = ";
  std::for_each(b.data, b.data + b.size, display);
  std::cout << "\tcopy of a" << std::endl;

  // Add a to b
  b += a;

  std::cout << "new b = ";
  std::for_each(b.data, b.data + b.size, display);
  std::cout << "\tb += a" << std::endl;
}

```

If you are really trying to push the envelope, take a peek at the source code for memcpy().  I doubt it is possible to make that code any more efficient.

P.S.  Unless you are working with a processor that is running slower than, say, 500Mhz, I really do not see why you are so concerned about the speed.  How many numbers will your arrays have?

---

### Post by dwhitney67 on 2009-04-08
> **Habbit said:**
> If you want to do things more complex than adding items, why not use the STL algorithms/functors? In this example I just try to add the items, but you can use any function you like:

```
#include <algorithm>
#include <functional>

// ...
// a and b are two of your special arrays
// ntm is the total number of elements (rows x cols)

std::transform(a[0], a[0] + ntm, b[0], b[0], std::plus<int>());

// equivalent to " b[0][i] += a[0][i] for each i in [0,ntm); "


```

That's pretty cool; I tried on my system and it worked!  Also found out that the array subscript [0] is not necessary.  I always thought that the STL algorithms only worked on iterators.

EDIT:  Take that back; I do need the array subscript if dealing with 2-dim arrays.

---

### Post by soltanis on 2009-04-08
Okay, so a C multi-dimensional array is really like a big one-dimensional array in memory. Diagram:

```

int array[3][2];

```

Somewhere in memory we have this
| int | int | int | int | int | int |

Accessing the 3rd column in the 2nd row (or other way around) actually accesses (at least for gcc) the 3 * 2 = 6th element in the one dimensional array that has the same number of elements as your 2D one.

You have to play a nasty trick on GCC to get it to cooperate:
```

int array[3][2];
int *p;

p = array; /* now p points to the first element of the array */

/* does not work:
array[5] = 1;
but this does, */

*(p+5) = 1;

if (array[2][1] == 1) /* you bet it does */

```

This generates a warning of an incompatible pointer type assignment. Thank God C isn't a type-nazi, or that might've not worked.

EDIT.

I cry for you sir, for I have now realized you are using C++ indeed.
No respectable (or at least, standards-conforming) C++ compiler will allow that code to fly:

```

g++ test.c
test.c: In function ‘int main()’:
test.c:7: error: cannot convert ‘int [3][2]’ to ‘int*’ in assignment

```

Perhaps surrounding the section in 'extern "C" { }' may let you get away with it, or perhaps not.[HTML][/HTML]

---

### Post by Habbit on 2009-04-08
> **dwhitney67 said:**
> I always thought that the STL algorithms only worked on iterators.

Well, actually it's working on iterators: pointers fulfill the requisites of a "random access iterator". Notice that the first two arguments to transform() are a [start, end) range: the address of the first element of the array, and an address "one past" the last element. The other two iterator ranges "input2" and "result" only require a start point because the length is assumed to be that of the first range.

Furthermore, you could achieve other results just by substituting the "T std:: plus<T>(T,T)" function for any other binary function, including a custom one (assume that arr1 and arr2 are arrays of float, with c and d already alloc'ed to receive the results):

```

// Function that returns the area of an ellipse given its major and minor axes
float elarea(float a, float b) {
    return 3.14159625f * a * b;
}

// Same thing, but with a functor object
class ElArea : public std::binary_function<float, float, float> {
public:
    float operator() (float a, float b) {
        return 3.14159625f * a * b;
    }
};

transform(a, a+n, b, c, elarea);   // Using function pointer
transform(a, a+n, b, d, ElArea()); // Using functor object

```

---

### Post by dwhitney67 on 2009-04-08
> **soltanis said:**
> ...
EDIT.

I cry for you sir, for I have now realized you are using C++ indeed.
No respectable (or at least, standards-conforming) C++ compiler will allow that code to fly:

```

g++ test.c
test.c: In function ‘int main()’:
test.c:7: error: cannot convert ‘int [3][2]’ to ‘int*’ in assignment

```

Perhaps surrounding the section in 'extern "C" { }' may let you get away with it, or perhaps not.
Where there's a will, there's a way...
```

#include <algorithm>
#include <iostream>

void disp(const int val)
{
  std::cout << val << " ";
}

int main()
{
  int a[3][2] = { {1,2}, {3, 4}, {5,6} };

  int* p = reinterpret_cast<int*>(a);

  std::for_each(p, p + 6, disp);
  std::cout << std::endl;
}

```

---

### Post by Habbit on 2009-04-08
> **soltanis said:**
> This generates a warning of an incompatible pointer type assignment. Thank God C isn't a type-nazi, or that might've not worked.

EDIT.

I cry for you sir, for I have now realized you are using C++ indeed.
No respectable (or at least, standards-conforming) C++ compiler will allow that code to fly:

```

g++ test.c
test.c: In function &#8216;int main()&#8217;:
test.c:7: error: cannot convert &#8216;int [3][2]&#8217; to &#8216;int*&#8217; in assignment

```

Perhaps surrounding the section in 'extern "C" { }' may let you get away with it, or perhaps not.[HTML][/HTML]

Well, why don't you do either of these?```
int array[2][3] = {...};
int* p;

p = &array[0][0];
p = reinterpret_cast<int*>(array);
```
Both do the trick. Nevertheless, it seems clear that C++ adamantly thinks that int[N][M] should not be converted to int* without at least a warning. Maybe there are some padding/alignment issues that are just not manifesting themselves with our current platforms?

EDIT: Whoops. I got beaten to it. So much for actually checking my code with g++ u_u. Well, it's time for me to go to bed ^^

---

### Post by soltanis on 2009-04-08
No way, the compiler is always wrong (especially when it tells you something about incompatible types. Then it's definitely wrong).

You're right though; at least from pure C standpoint, multidimensional arrays are implementation defined (like structs).

Speaking of structs, this would've also worked:

```

struct copy_me {
 int array[5][5];
}

struct copy_me one, two;
/* init */

two = one;

```

Both C and C++ I believe copy structs for you. No idea on how that factors in speed-wise, and you probably wont be allowed to do that if you're working in a team anyway.

---

### Post by Ultra Magnus on 2009-04-09
Thanks for all the replys, I'll have a mess around and see what best suits what I'm trying to do. Thanks again, James

---

### Post by Arndt on 2009-04-09
[QUOTE=Ultra Magnus;7036700]Hi, I was just wondering if anyone could give me a hand.

I'm writing a bit of code using allot of arrays and I've found that having something of the form

```

for (i = 0 ; i < n ; ++i)
{
    *a++ = *b++
}

```

is quicker than

```

for (i = 0 ; i < n ; ++i)
{
    a[i] = b[i] ;
}

```


How much faster? I think when using optimization in the compiler, they ought to come out the same.

---

### Post by soltanis on 2009-04-09
T Arndt, the expressions are supposedly equivalent, I have no idea why one would be faster than the other. Maybe he didn't turn on optimizations (or use the right one?)

---

