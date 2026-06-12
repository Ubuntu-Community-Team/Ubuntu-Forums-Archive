---
title: "32 bit C++ problem on amd64 - std lib includes missing?"
date: 2005-11-24
forum: Programming Talk
---

### Post by hopper on 2005-11-24
****************************************************************
posted on a sub-forum and bugzilla but no replies anywhere yet :???: 
****************************************************************

Hi all

I am using 5.10 amd64 to build a bunch of C & C++ code. All development and library packages are included (as far as I know) including the 'ia32' 32-bit libraries. All C and C++ builds are fine with both gcc-3.4 and gcc-4.0 on amd64. C code compiles, links and runs fine on 32-bit too. However, C++ will not even compile:

    /usr/include/c++/4.0.2/iostream:43:28: error: bits/c++config.h: No such file or directory
    In file included from /usr/include/c++/4.0.2/ios:43,
    from /usr/include/c++/4.0.2/ostream:44,
    from /usr/include/c++/4.0.2/iostream:44,
    from bgp_objects.cpp:10:
    /usr/include/c++/4.0.2/iosfwd:45:29: error: bits/c++locale.h: No such file or directory
    /usr/include/c++/4.0.2/iosfwd:46:25: error: bits/c++io.h: No such file or directory

    etc.. etc..

I believe this is because the 32-bit C++ standard library includes are not present:

    mwh $ locate bits/c++io
    /usr/lib/gcc/i586-mingw32msvc/3.4.2/include/c++/i586-mingw32msvc/bits/c++io.h
    /usr/include/c++/3.4/x86_64-linux-gnu/bits/c++io.h
    /usr/include/c++/4.0.2/x86_64-linux-gnu/bits/c++io.h

Have I missed something or is this a problem with the package installer setup? Is there a straightforward workaround?

TIA

Michael

---

