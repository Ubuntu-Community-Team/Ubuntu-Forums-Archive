---
title: "C++/Boost linker errors"
date: 2008-08-22
forum: Programming Talk
---

### Post by calzakk on 2008-08-22
Hi all,

I've got this really simple C++ program that's using the Boost.Filesystem library:
```
#include <iostream>
#include <boost/filesystem.hpp>

int main()
{
    boost::filesystem::path pathname = "/usr/local/bin";
    std::cout << pathname.string() << std::endl;
    return 0;
}
```
It compiles fine, and I can get it to link to the shared object:
[INDENT]g++ -I/usr/local/include/boost-1_35 -o test test.cpp -lboost_filesystem-gcc42-mt-1_35[/INDENT]
But I want to statically link instead. I've tried this and all sorts of similar commands:
[INDENT]g++ -I/usr/local/include/boost-1_35 -o test test.cpp -lboost_filesystem-gcc42-mt-s-1_35 -static -static-libgcc [/INDENT]
and I'm always getting these linker errors:
```
/tmp/ccoiFv2v.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x1dc): undefined reference to `boost::system::get_system_category()'
test.cpp:(.text+0x1e6): undefined reference to `boost::system::get_posix_category()'
test.cpp:(.text+0x1f0): undefined reference to `boost::system::get_posix_category()'
test.cpp:(.text+0x1fa): undefined reference to  `boost::system::get_system_category()'
collect2: ld returned 1 exit status
```
I've built Boost in full, and have got these Boost.Filesystem libraries in /usr/local/lib:
[INDENT]libboost_filesystem-gcc42-1_35.a
libboost_filesystem-gcc42-1_35.so
libboost_filesystem-gcc42-1_35.so.1.35.0
libboost_filesystem-gcc42.a
libboost_filesystem-gcc42-d-1_35.a
libboost_filesystem-gcc42-d-1_35.so
libboost_filesystem-gcc42-d-1_35.so.1.35.0
libboost_filesystem-gcc42-d.a
libboost_filesystem-gcc42-d.so
libboost_filesystem-gcc42-mt-1_35.a
libboost_filesystem-gcc42-mt-1_35.so
libboost_filesystem-gcc42-mt-1_35.so.1.35.0
libboost_filesystem-gcc42-mt.a
libboost_filesystem-gcc42-mt-d-1_35.a
libboost_filesystem-gcc42-mt-d-1_35.so
libboost_filesystem-gcc42-mt-d-1_35.so.1.35.0
libboost_filesystem-gcc42-mt-d.a
libboost_filesystem-gcc42-mt-d.so
libboost_filesystem-gcc42-mt-s-1_35.a
libboost_filesystem-gcc42-mt-s.a
libboost_filesystem-gcc42-mt-sd-1_35.a
libboost_filesystem-gcc42-mt-sd.a
libboost_filesystem-gcc42-mt.so
libboost_filesystem-gcc42-s-1_35.a
libboost_filesystem-gcc42-s.a
libboost_filesystem-gcc42-sd-1_35.a
libboost_filesystem-gcc42-sd.a
libboost_filesystem-gcc42.so[/INDENT]
I hope someone can help me because I just can't see what I'm doing wrong! :confused:

Thanks in advance,

cal

---

### Post by dwhitney67 on 2008-08-22
I believe the -static should come before the -l option.

Also, what is the difference between these libraries?  Are you certain you are specifying the correct one?
[LIST]
[*]libboost_filesystem-gcc42-1_35.a
[*]libboost_filesystem-gcc42.a
[*]libboost_filesystem-gcc42-d-1_35.a
[*]libboost_filesystem-gcc42-d.a
[*]libboost_filesystem-gcc42-mt-1_35.a
[*]libboost_filesystem-gcc42-mt.a
[*]libboost_filesystem-gcc42-mt-d-1_35.a
[*]libboost_filesystem-gcc42-mt-d.a
[*]libboost_filesystem-gcc42-mt-s-1_35.a
[*]libboost_filesystem-gcc42-mt-s.a
[*]libboost_filesystem-gcc42-mt-sd-1_35.a
[*]libboost_filesystem-gcc42-mt-sd.a
[*]libboost_filesystem-gcc42-s-1_35.a
[*]libboost_filesystem-gcc42-s.a
[*]libboost_filesystem-gcc42-sd-1_35.a
[*]libboost_filesystem-gcc42-sd.a
[/LIST]

---

### Post by calzakk on 2008-08-31
If anyone's interested...
I had to link to boost_system-gcc42-mt-1_35 too - D'oh!!!
(The clue is in the linker errors - boost::_system_::get_system_category() etc.)

So the correct build command is:
[INDENT]g++ -I/usr/local/include/boost-1_35 -o test test.cpp -lboost_filesystem-gcc42-mt-s-1_35 -lboost_system-gcc42-mt-s-1_35 -static[/INDENT]

---

### Post by dribeas on 2008-08-31
> **calzakk said:**
> But I want to statically link instead. I've tried this and all sorts of similar commands:
[INDENT]g++ -I/usr/local/include/boost-1_35 -o test test.cpp -lboost_filesystem-gcc42-mt-s-1_35 -static -static-libgcc [/INDENT]


Try giving the full name of the lib as in:
[INDENT]g++ -I/usr/local/include/boost-1_35 -o test test.cpp -l:libboost_filesystem-gcc42-mt-s-1_35.a -static -static-libgcc [/INDENT]

---

### Post by AugustinMa on 2010-08-13
I had a very similar problem and found this post while searching. I managed to solved the problem after much more searching, so I post it here for other people.
 
 I had to link to the proper library this way:
 g++ boost_example.cpp -o run -lboost_filesystem-mt
 [http://linux.overshoot.tv/ticket/127](http://linux.overshoot.tv/ticket/127)
 
 The real problem is that the boost documentation is lacking and does not say which library to link to. See:
 [http://linux.overshoot.tv/ticket/129](http://linux.overshoot.tv/ticket/129)
 
 Anyway, to use boost/file_system, link to: -lboost_filesystem-mt .

See also:
[http://ubuntuforums.org/showthread.php?t=244593](http://ubuntuforums.org/showthread.php?t=244593)

---

