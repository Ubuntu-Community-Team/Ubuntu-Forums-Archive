---
title: "C++ Compiler errors"
date: 2008-04-25
forum: Packaging and Compiling Programs
---

### Post by dubnde on 2008-04-25
I need some help figuring out what causes this compiler error. These are standard header files and I have not touched them. The same program compiles on a different machine but fails on ubuntu 8.04. Not sure if it has anything to do with ubuntu but any kind of help questions may trigger something.

/usr/include/c++/4.2/fstream:100: error: cannot declare `ios_base::openmode' within `basic_filebuf'
/usr/include/c++/4.2/bits/fstream.tcc:49: error: `_M_allocate_internal_buffer' is not a member of `basic_filebuf'

--------------
g++ (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

---

### Post by kikazaru on 2008-05-20
Similar problems when I try to compile SWIFT++. Is there some backwards compatibility mode that will let me compile this? What's going on...?

In file included from /usr/include/c++/4.2/fstream:805,
                 from /usr/include/c++/4.2/backward/fstream.h:32,
                 from ../include/SWIFT_fileio.h:56,
                 from scene.cpp:62:
/usr/include/c++/4.2/bits/fstream.tcc: In member function &#8216;virtual typename std::basic_filebuf<_CharT, _Traits>::int_type std::basic_filebuf<_CharT, _Traits>::underflow()&#8217;:
/usr/include/c++/4.2/bits/fstream.tcc:289: error: expected unqualified-id before &#8216;(&#8217; token
/usr/include/c++/4.2/bits/fstream.tcc: In member function &#8216;virtual std::streamsize std::basic_filebuf<_CharT, _Traits>::xsputn(const _CharT*, std::streamsize)&#8217;:
/usr/include/c++/4.2/bits/fstream.tcc:612: error: expected unqualified-id before &#8216;(&#8217; token

I also tried installing g++-3.4 but I get exactly the same problem:

In file included from /usr/include/c++/3.4/fstream:840,
                 from /usr/include/c++/3.4/backward/fstream.h:32,
                 from ../include/SWIFT_fileio.h:56,
                 from scene.cpp:62:
/usr/include/c++/3.4/bits/fstream.tcc: In member function `virtual typename std::basic_filebuf<_CharT, _Traits>::int_type std::basic_filebuf<_CharT, _Traits>::underflow()':
/usr/include/c++/3.4/bits/fstream.tcc:277: error: expected unqualified-id before '(' token
/usr/include/c++/3.4/bits/fstream.tcc: In member function `virtual std::streamsize std::basic_filebuf<_CharT, _Traits>::xsputn(const _CharT*, std::streamsize)':
/usr/include/c++/3.4/bits/fstream.tcc:600: error: expected unqualified-id before '(' token

---

### Post by kikazaru on 2008-05-20
This was due to: 

#define min ...
#define max ...

in the code I was trying to compile conflicting with std::min and std::max in those standard files. I guess it might be something else in your case, but just look at the line of the standard file to find out what is conflicting.

---

