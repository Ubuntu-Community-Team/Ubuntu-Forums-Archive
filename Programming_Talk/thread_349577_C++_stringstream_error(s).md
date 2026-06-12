---
title: "C++ stringstream error(s)"
date: 2007-01-30
forum: Programming Talk
---

### Post by Cheiron on 2007-01-30
I'm having some real problems with the stringstream classes. I'm trying to convert an integer to a string using the code

```

#include <sstream>
...
std::ostringstream ss;
std::string str;
ss << 1;
str = ss.str();
...

```

When I try to compile with g++, I get a torrent of error messages.

```

/usr/lib/gcc/i486-linux-gnu/4.1.2/include/stddef.h:152: error: expected constructor, destructor, or type conversion before &#8216;typedef&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstddef:54: error: &#8216;::ptrdiff_t&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/postypes.h:78: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:104: error: expected type-specifier before &#8216;ptrdiff_t&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:104: error: expected `>' before &#8216;ptrdiff_t&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:115: error: &#8216;_Pointer&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:117: error: &#8216;_Reference&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:141: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:151: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator.h:97: error: wrong number of template arguments (5, should be 3)
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:106: error: provided for &#8216;template<class _Category, class _Tp, class _Distance> struct std::iterator&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator.h:384: error: wrong number of template arguments (5, should be 3)
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:106: error: provided for &#8216;template<class _Category, class _Tp, class _Distance> struct std::iterator&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator.h:459: error: wrong number of template arguments (5, should be 3)
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:106: error: provided for &#8216;template<class _Category, class _Tp, class _Distance> struct std::iterator&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator.h:537: error: wrong number of template arguments (5, should be 3)
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:106: error: provided for &#8216;template<class _Category, class _Tp, class _Distance> struct std::iterator&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_algobase.h: In static member function &#8216;static _Tp* std::__copy_backward<true, std::random_access_iterator_tag>::copy_b(const _Tp*, const _Tp*, _Tp*)&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_algobase.h:424: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_algobase.h:425: error: &#8216;_Num&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/ext/new_allocator.h: At global scope:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/ext/new_allocator.h:54: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/allocator.h:65: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/allocator.h:86: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_raw_storage_iter.h:72: error: wrong number of template arguments (5, should be 3)

```

This is just the first little bit. The whole thing runs off the top of the terminal window.

I have build-essential installed, and other programmes compile without error in g++, just so long as they don't use <sstream>

I have libstdc++6-4.1-dev installed.

Anyone have any idea what is causing this?

Thanks.

---

### Post by hod139 on 2007-01-30
Running dapper your posted code snippet built fine for me.

---

### Post by Cheiron on 2007-01-30
I'm running edgy. I've had this kind of code build properly on other systems using g++, so I'm fairly certain that it's a configuration problem and not a code problem - I just don't know what it is...

---

### Post by hod139 on 2007-01-31
Works for me in edgy.  Just out of curiosity, you have installed the  build-essential package right?

---

### Post by christian.convey on 2007-02-14
> **Cheiron said:**
> I'm having some real problems with the stringstream classes. I'm trying to convert an integer to a string using the code

```

#include <sstream>
...
std::ostringstream ss;
std::string str;
ss << 1;
str = ss.str();
...

```

When I try to compile with g++, I get a torrent of error messages.

```

/usr/lib/gcc/i486-linux-gnu/4.1.2/include/stddef.h:152: error: expected constructor, destructor, or type conversion before &#8216;typedef&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstddef:54: error: &#8216;::ptrdiff_t&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/postypes.h:78: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:104: error: expected type-specifier before &#8216;ptrdiff_t&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:104: error: expected `>' before &#8216;ptrdiff_t&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:115: error: &#8216;_Pointer&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:117: error: &#8216;_Reference&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:141: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:151: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator.h:97: error: wrong number of template arguments (5, should be 3)
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:106: error: provided for &#8216;template<class _Category, class _Tp, class _Distance> struct std::iterator&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator.h:384: error: wrong number of template arguments (5, should be 3)
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:106: error: provided for &#8216;template<class _Category, class _Tp, class _Distance> struct std::iterator&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator.h:459: error: wrong number of template arguments (5, should be 3)
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:106: error: provided for &#8216;template<class _Category, class _Tp, class _Distance> struct std::iterator&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator.h:537: error: wrong number of template arguments (5, should be 3)
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_iterator_base_types.h:106: error: provided for &#8216;template<class _Category, class _Tp, class _Distance> struct std::iterator&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_algobase.h: In static member function &#8216;static _Tp* std::__copy_backward<true, std::random_access_iterator_tag>::copy_b(const _Tp*, const _Tp*, _Tp*)&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_algobase.h:424: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_algobase.h:425: error: &#8216;_Num&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/ext/new_allocator.h: At global scope:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/ext/new_allocator.h:54: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/allocator.h:65: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/allocator.h:86: error: &#8216;ptrdiff_t&#8217; does not name a type
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/stl_raw_storage_iter.h:72: error: wrong number of template arguments (5, should be 3)

```

This is just the first little bit. The whole thing runs off the top of the terminal window.

I have build-essential installed, and other programmes compile without error in g++, just so long as they don't use <sstream>

I have libstdc++6-4.1-dev installed.

Anyone have any idea what is causing this?

Thanks.
Your code snippet runs fine on my Edgy box, **BUT...**

I have another piece of code (it's not concise enough for a test case yet) that gets the very same errors you're showing.  Have you figured out what was causing it for *you*?

Thanks,
Christian

---

