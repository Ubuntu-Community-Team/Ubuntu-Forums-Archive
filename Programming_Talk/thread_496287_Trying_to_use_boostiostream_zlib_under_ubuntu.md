---
title: "Trying to use boost::iostream zlib under ubuntu"
date: 2007-07-09
forum: Programming Talk
---

### Post by yinglcs2 on 2007-07-09
Hi,

I am trying to compile the following boost::iostream zlib program under ubuntu.  but I get linker error:

Can someone please help me try to get it to work under ubuntu?

Code:

```
#include <fstream>
#include <iostream>
#include <boost/iostreams/filtering_streambuf.hpp>
#include <boost/iostreams/copy.hpp>
#include <boost/iostreams/filter/zlib.hpp>


    
    int main()
    {
        using namespace std;
        using namespace boost::iostreams; // Added this line.
        ifstream file("hello.z", ios_base::in | ios_base::binary);
        filtering_streambuf<input> in;
        in.push(zlib_decompressor());
            in.push(file);
            
            boost::iostreams::copy(in, cout);
    }
```

Here is the error:

```

**** Build of configuration Debug for project boostTest ****

make all 
Building target: boostTest
Invoking: GCC C++ Linker
g++  -o"boostTest"  ./src/boostTest.o   
./src/boostTest.o: In function `void boost::iostreams::detail::zlib_base::init<std::allocator<char> >(boost::iostreams::zlib_params const&, bool, boost::iostreams::detail::zlib_allocator<std::allocator<char>, boost::iostreams::detail::zlib_allocator_traits<std::allocator<char> >::type>&)':
/usr/include/boost/iostreams/filter/zlib.hpp:182: undefined reference to `boost::iostreams::detail::zlib_base::do_init(boost::iostreams::zlib_params const&, bool, void* (*)(void*, unsigned int, unsigned int), void (*)(void*, void*), void*)'
./src/boostTest.o: In function `zlib_decompressor_impl':
/usr/include/boost/iostreams/filter/zlib.hpp:363: undefined reference to `boost::iostreams::detail::zlib_base::zlib_base()'
/usr/include/boost/iostreams/filter/zlib.hpp:365: undefined reference to `boost::iostreams::zlib::default_strategy'
/usr/include/boost/iostreams/filter/zlib.hpp:365: undefined reference to `boost::iostreams::zlib::deflated'
/usr/include/boost/iostreams/filter/zlib.hpp:365: undefined reference to `boost::iostreams::zlib::default_compression'
/usr/include/boost/iostreams/filter/zlib.hpp:367: undefined reference to `boost::iostreams::detail::zlib_base::~zlib_base()'
./src/boostTest.o: In function `~zlib_decompressor_impl':
/usr/include/boost/iostreams/filter/zlib.hpp:360: undefined reference to `boost::iostreams::detail::zlib_base::reset(bool, bool)'
/usr/include/boost/iostreams/filter/zlib.hpp:360: undefined reference to `boost::iostreams::detail::zlib_base::~zlib_base()'
/usr/include/boost/iostreams/filter/zlib.hpp:360: undefined reference to `boost::iostreams::detail::zlib_base::~zlib_base()'
./src/boostTest.o: In function `boost::iostreams::detail::zlib_decompressor_impl<std::allocator<char> >::close()':
/usr/include/boost/iostreams/filter/zlib.hpp:383: undefined reference to `boost::iostreams::detail::zlib_base::reset(bool, bool)'
./src/boostTest.o: In function `boost::iostreams::detail::zlib_decompressor_impl<std::allocator<char> >::filter(char const*&, char const*, char*&, char*, bool)':
/usr/include/boost/iostreams/filter/zlib.hpp:375: undefined reference to `boost::iostreams::detail::zlib_base::before(char const*&, char const*, char*&, char*)'
/usr/include/boost/iostreams/filter/zlib.hpp:376: undefined reference to `boost::iostreams::zlib::sync_flush'
/usr/include/boost/iostreams/filter/zlib.hpp:376: undefined reference to `boost::iostreams::detail::zlib_base::inflate(int)'
/usr/include/boost/iostreams/filter/zlib.hpp:377: undefined reference to `boost::iostreams::detail::zlib_base::after(char const*&, char*&, bool)'
/usr/include/boost/iostreams/filter/zlib.hpp:378: undefined reference to `boost::iostreams::zlib_error::check(int)'
/usr/include/boost/iostreams/filter/zlib.hpp:379: undefined reference to `boost::iostreams::zlib::stream_end'
collect2: ld returned 1 exit status
make: *** [boostTest] Error 1


```

---

### Post by nevelis on 2009-02-15
I know this post is years old, but it messed me up for a while.

You need to link the libboost_iostreams library when you link your object files.  Add -lboost_iostreams to dynamically link, eg: 

```
g++ -o something -lboost_iostreams something.cpp
```

or to statically link, you must link in zlib...

```
g++ -o something -lz /usr/lib/libboost_iostreams.a something.cpp
```

Hopefully this will save someone else pulling their hair out!

Cheers

---

### Post by dwhitney67 on 2009-02-15
Anytime you link C or C++ object file(s), and you come across an "undefined reference", this generally means one of two things:

1)  The developer failed to implement a particular function/method; or

2)  The developer forgot to link in a library that contains the missing function/method implementation.

On rare occasions, I have had issues specifying a library before my object file in a gcc (or g++) statement.  I recommend that one follow this style:
```

g++ <.cpp or .o file(s)> [LDFLAGS] [LIBS] -o [appname]

```
The placement of the -o and its corresponding arg are not really relevant, as long as they remain together.

---

### Post by alberthendriks on 2011-07-16
> **nevelis said:**
> Hopefully this will save someone else pulling their hair out!
It did. Long live internet history. Thanks!

---

### Post by noobinabox on 2012-11-06
> **alberthendriks said:**
> It did. Long live internet history. Thanks!

Same here! Thanks!

---

