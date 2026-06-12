---
title: "How to find libraries that implement header files?"
date: 2008-05-17
forum: Programming Talk
---

### Post by MalcolmCarmen on 2008-05-17
edit: this issue is **resolved**!

I'm new to C++, and wanted to try dynamic library loading (I'm on Hardy, which seems to already have build-essential and g++). I planned to do this with the functions defined in dlfcn.h ([http://www.opengroup.org/onlinepubs/009695399/basedefs/dlfcn.h.html](http://www.opengroup.org/onlinepubs/009695399/basedefs/dlfcn.h.html)).

I certainly have the header file dlfcn.h, but it appears it can't be linked:
/home/ds/C++/TestApp/testmain.cpp:8: undefined reference to `dlopen'
/home/ds/C++/TestApp/testmain.cpp:11: undefined reference to `dlsym'

(these are functions defined in dlfcn.h)

I've been googling for a good while and can't determine how to actually find a library on my system that provides this functionality so that I can provide g++ the location.

If I've skipped something elementary that I should have already known, I'll be glad to go over that instead!

The code:
```

#include <dlfcn.h>
#include <iostream>
using namespace std;

int main () {    
    char *filename = "/home/ds/C++/TestLibrary/dist/Debug/GNU-Linux-x86/libTestLibrary.so";
    
    void *library = dlopen(filename, RTLD_NOW);    
    cout << "successfully opened " << filename << endl;
    
    void *TestRetPtr = dlsym(library, "TestFunction");
    
    return 0;
}

```

---

### Post by LaRoza on 2008-05-17
```

~$apt-cache search dlopen
exim4-daemon-light - lightweight Exim MTA (v4) daemon
libhx-dev - Development files for libhx
libhx10 - A library providing queue, tree, I/O and utility functions
libltdl3 - A system independent dlopen wrapper for GNU libtool
libltdl3-dev - A system independent dlopen wrapper for GNU libtool
libcxxtools-dev - library of unrelated but useful C++ classes
libcxxtools4 - library of unrelated but useful C++ classes
~$

```

*-dev are the development files. Install those that you need.

---

### Post by MalcolmCarmen on 2008-05-17
Thank you very much, I installed 'libltdl3-dev' and specified '-lltdl' for g++ and it works perfectly!

---

