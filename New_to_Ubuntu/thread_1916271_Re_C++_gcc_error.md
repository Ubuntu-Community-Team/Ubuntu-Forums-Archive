---
title: "Re: C++ gcc error"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by nozarm on 2012-01-27
I am seeing a g++/c++ compilatin error after an upgrade to 11.10



c++ -c  -W -Wall -Wcast-align -Wcast-qual -Wextra -Wformat -Wpointer-arith -Wredundant-decls -Wshadow -Wno-write-strings -DUNIX -fwrapv -fno-strict-aliasing -fPIC -m32 -O3 -funroll-loops -g -DNDEBUG -D_DEBUG=0 -I/usr/include -I/usr/include/python2.7 array.cc

c++: error trying to exec 'cc1plus': execvp: No such file or directory
=======================================================================

locate cc1plus: 
/usr/lib/gcc/i686-linux-gnu/4.6/cc1plus

g++ --version:
g++ (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


gcc --version:
gcc (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Does anyone know what is going on?  Why can't 
/usr/bin/g++-4.6 find cc1plus???


I have been struggling with this for few days.  Have reinstalled build-essential, and no change!

Thanks,
Mina

---

### Post by howefield on 2012-01-27
Post moved to it's own thread.

Thank you.

---

