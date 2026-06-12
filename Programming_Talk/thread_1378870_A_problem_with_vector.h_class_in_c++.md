---
title: "A problem with vector.h class in c++"
date: 2010-01-11
forum: Programming Talk
---

### Post by zarzor_2010 on 2010-01-11
Hi all
Please , can you help me solving this problem
I have been searching google for the last week without a good answer

I have the following construcor function in GlobalState class

std::vector<double *> iL_data;
  std::vector<double *> iC_data;

GlobalState(int n_iterations, int n_blocks, int n_lines, int n_sections,
              double sim_size, int n_points, double x, LineParams &rlcg) :
    n_iterations(n_iterations),
    n_blocks(n_blocks),
    n_lines(n_lines),
    n_sections(n_sections),
    n_points(n_points),
    n_points_per_block(n_points / n_blocks),
    t_data(n_blocks, std::vector<double>((n_points / n_blocks) + 1)),
    data_node((n_iterations-1)*n_blocks*n_lines*n_sections, 0),
    vL_data((n_iterations-1)*n_blocks*n_lines*n_sections, (double *)NULL),
    **iL_data((n_iterations-1)*n_blocks*n_lines*n_sections, NULL),**
    **iC_data((n_iterations-1)*n_blocks*n_lines*n_sections, NULL),**
    time_axis(n_points+1),
    near_result(n_lines, std::vector<double>(n_points+1)),
    far_result(n_lines, std::vector<double>(n_points+1))


 When I try to compile this in g++ 4.3 the following error appears/usr/include/c++/4.3/bits/stl_vector.h:290:   instantiated from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const _Alloc&) [with _InputIterator = int, _Tp = double*, _Alloc = std::allocator<double*>]’
relax_lumped.h:216:   instantiated from here
/usr/include/c++/4.3/bits/stl_vector.h:932: error: invalid conversion from ‘int’ to ‘double*’
/usr/include/c++/4.3/bits/stl_vector.h:932: error:   initializing argument 2 of ‘void std::vector<_Tp, _Alloc>::_M_fill_initialize(size_t, const _Tp&) [with _Tp = double*, _Alloc = std::allocator<double*>]’
make[2]: *** [relax_lumped-relax_lumped.o] Error 1
m
whererelax_lumped.h:216 and 217 are the bold lines in the code
I have compiled this code in gentoo
but doesnt compile in ubuntuPlease, can you help me on this issue
I have been stuck in this problem for a while



Thanks alot
really appreciat it
Mina

---

### Post by Simon17 on 2010-01-12
```

vL_data((n_iterations-1)*n_blocks*n_lines*n_sections, (double *)NULL),
iL_data((n_iterations-1)*n_blocks*n_lines*n_sections, NULL),
iC_data((n_iterations-1)*n_blocks*n_lines*n_sections, NULL),

```

Which compiler version? What flags are you using?
You should see if nullptr is defined and use that instead of NULL as NULL is now deprecated.

---

### Post by MadCow108 on 2010-01-12
why not solve it, like in the line above, with casting?
vL_data((n_iterations-1)*n_blocks*n_lines*n_sections, (double *)NULL)
(or use static_cast<double*>(NULL))

the problem is that in pre-c++0x no nullpointer type exists, only a define of 0 to NULL which is an int

---

### Post by miklcct on 2010-01-12
> **Simon17 said:**
> ```

vL_data((n_iterations-1)*n_blocks*n_lines*n_sections, (double *)NULL),
iL_data((n_iterations-1)*n_blocks*n_lines*n_sections, NULL),
iC_data((n_iterations-1)*n_blocks*n_lines*n_sections, NULL),

```

Which compiler version? What flags are you using?
You should see if nullptr is defined and use that instead of NULL as NULL is now deprecated.

NULL is not deprecated, NULL may be defined as nullptr.

---

### Post by zarzor_2010 on 2010-01-12
Hi all
Thank you so much for your answers

I am using gcc 4.3 in ubuntu, which is the last gcc version available in ubuntu


The problem is that the code contains many vectors that are declared like

**iL_data((n_iterations-1)*n_blocks*n_lines*n_sections, NULL),**

and I cant go after them one by one, it would be a disaster

But what is confusing me, this code was working in gentoo gcc 4.4

Is there any update or a fix for Ubuntu gcc 4.3 to correct for Null pointers

Thank you so much again for your reply anf for helping me in this matter

Thanks
Mina

---

### Post by zarzor_2010 on 2010-01-12
I have just tried nullptr, and it is not defined 

Thanks
Mina

---

### Post by dwhitney67 on 2010-01-12
> **zarzor_2010 said:**
> 
The problem is that the code contains many vectors that are declared like

**iL_data((n_iterations-1)*n_blocks*n_lines*n_sections, NULL),**

and I cant go after them one by one, it would be a disaster


Sorry to hear that, but there is nothing that can be done.  The API for the STL vector clearly specifies the parameters that are necessary for calling the version of the constructor you chose to use, and nowhere does it state that you can declare a vector using type T, and then provide it an alternate data type X for initializing the contents of the vector.

As mentioned earlier, NULL is defined to be 0 (zero), which is an int value.

Here's the link to the relevant documentation:
[http://www.cplusplus.com/reference/stl/vector/vector/](http://www.cplusplus.com/reference/stl/vector/vector/)

As for the 'nullptr', it's news to me as well.  There has been discussion of adding it to the C++0x standard, but that is as far as it has gone... at least on my system which has GCC 4.4.1.

Here's a Wiki discussion of 'nullptr':
[http://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/nullptr](http://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/nullptr)

Anyhow, in the time that you spend researching the issue with your code and hoping for a miracle to occur, I bet it would be easier to update your code to follow the STL API.

A quick fix, as mentioned earlier, is to cast your NULLs to a double-pointer.

For example:
```

std::vector<double*> vec(someSize, static_cast<double*>(NULL));

```

---

### Post by Habbit on 2010-01-12
> **dwhitney67 said:**
> As mentioned earlier, NULL is defined to be 0 (zero), which is an int value.

The problem is not 0. Zero itself (and specifically 0, not any other number) is recognized as a null pointer constant, and automagically casts to any pointer type. The problem is (most likely) that the OP's NULL macro is (re)defined somewhere as ((void*)0). Unlike in ANSI C, void* does _not_ implicitly cast to any T*, you have to force it.

Try it: the only errors in this program are lines 9 and 10 (g++ -ansi -pedantic)
```
#include <iostream>

using namespace std;

int main(int, char**) {
        void* v = 0;
        double* d = 0; // Perfectly legal
        std::ostream* str = 0; // For non-POD types too
        double* err = v; // Error: void* does not cast to double*
        long* err2 = ((void*)0); // Error: a common definition for NULL
        return 0;
}
``````
$ g++ -ansi -pedantic -Wconversion test.cc
test.cc: In function ‘int main(int, char**)’:
test.cc:9: error: invalid conversion from ‘void*’ to ‘double*’
test.cc:10: error: invalid conversion from ‘void*’ to ‘long int*’

```

---

### Post by dribeas on 2010-01-12
The problem is that the code is triggering a different constructor than the one the user wants. The user is probably expecting:

```

vector( size_t size, T const & value );

```

But the compiler is matching with (reading the compiler error helps here, first line):

```

template <typename Iterator>
vector( Iterator begin, Iterator end );

```

While a user will tell you right away that 'int' is not an iterator, for the compiler the fact that the template argument is 'Iterator' has no meaning at all. Since both arguments are of type 'int' the templated constructor becomes a better match than the non-templated version (that would require two casts). Casting either one of the two arguments, either the first argument to std::size_t or the second to double* will disqualify the templated constructor (the two arguments must be of the same type for the template to match), and that will force the compiler into implicitly casting the other argument.

This is one of the places where concepts as defined in some earlier C++0x drafts would have aided the library writer and user by disabling the templated constructor with 'int' not fulfilling the concept requirements for an Iterator. But that will have to wait for some more years to come.

Why did it work with gcc 4.4? Maybe the operations performed on the first argument yielded a different type than NULL (which in C++ should be defined as 0, that is: int) (32/64bit architectures?).

On the later question of how to update the compiler, I am quite sure that the repositories have gcc 4.4 or even 4.5 available. If you are running an older version of ubuntu you might want to upgrade to 9.10.

---

### Post by Habbit on 2010-01-12
> **dribeas said:**
> reading the compiler error helps
Indeed #-o

---

### Post by zarzor_2010 on 2010-01-15
Thank you so much for every one
I downloaded gcc 4.4 but the problem is still there
So, I think I had no other way but using (double*)NULL
I did that and it is working correctly

Thanks again
Mina

---

