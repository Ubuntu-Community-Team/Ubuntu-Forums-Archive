---
title: "Basic STL problems when Compiling on Ubuntu 8.10"
date: 2008-11-26
forum: Programming Talk
---

### Post by DBQ on 2008-11-26
Hi everybody.  I have just upgraded from ubuntu 8.04 to 8.10.  The code bellow worked perfectly on 8.04.  But gives me errors (shown bellow code) when I compile this on 8.10.  I am puzzled as to why.  Also, the full program has many other STL errors (which compiled fine in 8.04), but I want to take it one at a time.

Any ideas?  
```


struct stt
{
 
};
 
vector<vector<vector<stt> > > cube(1000, 1000);

```

g++ t.cpp -o t
/usr/include/c++/4.3/bits/stl_vector.h: In member function ‘void std::vector<_Tp, _Alloc>::_M_initialize_dispatch(_Integer, _Integer, std::__true_type) [with _Integer = int, _Tp = std::vector<std::vector<stt, std::allocator<stt> >, std::allocator<std::vector<stt, std::allocator<stt> > > >, _Alloc = std::allocator<std::vector<std::vector<stt, std::allocator<stt> >, std::allocator<std::vector<stt, std::allocator<stt> > > > >]’:
/usr/include/c++/4.3/bits/stl_vector.h:290:   instantiated from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const _Alloc&) [with _InputIterator = int, _Tp = std::vector<std::vector<stt, std::allocator<stt> >, std::allocator<std::vector<stt, std::allocator<stt> > > >, _Alloc = std::allocator<std::vector<std::vector<stt, std::allocator<stt> >, std::allocator<std::vector<stt, std::allocator<stt> > > > >]’
t.cpp:9:   instantiated from here
/usr/include/c++/4.3/bits/stl_vector.h:932: error: no matching function for call to ‘std::vector<std::vector<std::vector<stt, std::allocator<stt> >, std::allocator<std::vector<stt, std::allocator<stt> > > >, std::allocator<std::vector<std::vector<stt, std::allocator<stt> >, std::allocator<std::vector<stt, std::allocator<stt> > > > > >::_M_fill_initialize(size_t, int&)’
/usr/include/c++/4.3/bits/stl_vector.h:974: note: candidates are: void std::vector<_Tp, _Alloc>::_M_fill_initialize(size_t, const _Tp&) [with _Tp = std::vector<std::vector<stt, std::allocator<stt> >, std::allocator<std::vector<stt, std::allocator<stt> > > >, _Alloc = std::allocator<std::vector<std::vector<stt, std::allocator<stt> >, std::allocator<std::vector<stt, std::allocator<stt> > > > >]

---

### Post by dwhitney67 on 2008-11-26
> **DBQ said:**
> Hi everybody.  I have just upgraded from ubuntu 8.04 to 8.10.  The code bellow worked perfectly on 8.04.  But gives me errors (shown bellow code) when I compile this on 8.10.  I am puzzled as to why.  Also, the full program has many other STL errors (which compiled fine in 8.04), but I want to take it one at a time.

Any ideas?  
```


struct stt
{
 
};
 
vector<vector<vector<stt> > > cube(1000, 1000);

```
...
Your 8.04 system probably had GCC 4.2.4 installed on it, and now your newer system probably has GCC 4.3.0.

Your code does indeed compile under 8.04, however I am surprised it did.  The API for the std::vector does shows a constructor with the format similar to what you demonstrated, but since the type T you provided is not an int, it should not have worked.  See [here]("http://www.cplusplus.com/reference/stl/vector/vector.html").

This code snippet does compile with GCC 4.3.0:
[php]
...
std::vector< std::vector<STT> > val;

std::vector< std::vector< std::vector<STT> > > cube(1000, val);
...
[/php]

P.S. 'val' is of type T, which is the template value given to the exterior vector in the code above.

---

### Post by DBQ on 2008-11-26
Thank you for the reply!

hmmmm...but I did "using namespace std;" so that should have eliminated the need for "std::.."

---

### Post by dwhitney67 on 2008-11-26
I prefer to not specify "using namespace" in my code; it's a personal preference.

---

### Post by DBQ on 2008-11-26
Thats cool.  However, in this case it should not affect the correctness of the code.

---

