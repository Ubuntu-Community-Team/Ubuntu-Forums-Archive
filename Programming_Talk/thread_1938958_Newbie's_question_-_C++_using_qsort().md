---
title: "Newbie's question - C++ using qsort()"
date: 2012-03-10
forum: Programming Talk
---

### Post by chenxinghao on 2012-03-10
Installed Ubuntu 11.10 in January with all the defaults and added C++ compiler. I am learning C++ programming.

The qsort() function in the library doesn't seem to follow C++ classification/definition. In the qsort manpage, the example uses a cmpstringp function is also not defined with C++ classification/definition style.

My question is: 

(1) Are there C++ versions of qsort?  

(2) If not, what is the best way to "make" the library qsort function to C++ style?

Thanks.

---

### Post by Simian Man on 2012-03-10
qsort is inherited from C.  For C++, use [std::sort]("http://en.cppreference.com/w/cpp/algorithm/sort").

---

### Post by lisati on 2012-03-10
*Thread moved to **Programming Talk**.*

---

### Post by chenxinghao on 2012-03-10
The manpage for sort on Ubuntu doesn't seem to describe to provide the same functionality as those of the C qsort.

---

### Post by dwhitney67 on 2012-03-10
> **chenxinghao said:**
> 
My question is: 

(1) Are there C++ versions of qsort?  

(2) If not, what is the best way to "make" the library qsort function to C++ style?

What type of container (of your data) are you trying to sort?  C++ is quite capable of using library functions that are defined in the C library.

And what do you mean "C++ style"??

---

### Post by Simian Man on 2012-03-10
> **chenxinghao said:**
> The manpage for sort on Ubuntu doesn't seem to describe to provide the same functionality as those of the C qsort.
You are probably looking at the page for the Unix sort command, not the C++ function.  I don't know if there are man pages for the C++ standard library.  I use the site I linked you to for C++ library reference.

> **dwhitney67 said:**
> What type of container (of your data) are you trying to sort?  C++ is quite capable of using library functions that are defined in the C library.

And what do you mean "C++ style"??

You certainly can use qsort in C++, but std::sort is better for a number of reasons.  First it is more flexible in that it can sort arrays, vectors, strings, or deques - in addition to any containers you create yourself that provide iterators.

More importantly, std::sort is type safe because the templates are checked for correctness at compile time.  With qsort, the data is passed in as void pointers and cast at runtime which allows for segfaults if you aren't careful.

---

### Post by chenxinghao on 2012-03-10
The data I have is an array (or list) that its elements are to be sorted according to a defined function (the cmpstringp in qsort). I am looking for a similar qsort +cmpstringp in C++.

By "C++ style" I mean the sorting function is called upon with nodeA.myListSort(...) and nodeB.myListSprt(...), where myListSort is used on two different classes and sort list differently. (Each sort uses qsort with its own cmpstringp like compare function.)

I guess I can use a "shell" function to wrap around the C qsort function and hence make it (in this the sorting function) appear to be a C++ compliant definition. But a qsort from C++ library would simplify the code and more transparent.

Where to look for C++ library functions list?

---

### Post by MadCow108 on 2012-03-10
you can use the C qsort in C++ with no problems, just as any other C function.
just include #include <cstdlib>
[http://www.cplusplus.com/reference/clibrary/cstdlib/qsort/](http://www.cplusplus.com/reference/clibrary/cstdlib/qsort/)
compared to c++'s sorts, qsort only works with continuous memory blocks (= no lists)!

it is recommended to use the c++ variants, they are mostly simpler, less error prone, more flexible and can even be faster in some case (C++ functors are easier to inline)

here the random access sort, it works fine on C -style arrays (random access iterator == pointer):
[http://www.cplusplus.com/reference/algorithm/sort/](http://www.cplusplus.com/reference/algorithm/sort/)

non-random access containers like lists have their own sort:
[http://www.cplusplus.com/reference/stl/list/sort/](http://www.cplusplus.com/reference/stl/list/sort/)

---

