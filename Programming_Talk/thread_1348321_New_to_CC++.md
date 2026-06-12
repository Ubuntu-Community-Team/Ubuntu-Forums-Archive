---
title: "New to C/C++"
date: 2009-12-07
forum: Programming Talk
---

### Post by Lyon on 2009-12-07
I'm new to C/C++ and I've decided to try and learn it and use some libraries to hopefully make some useful programs.

I installed libcv-dev and all its related packages, but I don't seem to quite understand how to include it. From all of the tutorials I've seen,

```
#include "cv.h"
```

should do the trick. However, it keeps telling me the file is not found when I compile it in monodevelop. Also, when I search my system for cv.h, the only file that comes up is in a Perl directory.

Any help for a complete beginner?

Thanks

---

### Post by Zugzwang on 2009-12-07
Ok. So first look here:

[http://packages.ubuntu.com/karmic/i386/libcv-dev/filelist](http://packages.ubuntu.com/karmic/i386/libcv-dev/filelist)

The packages.ubuntu.com webpage is nice for getting information about packages in Ubuntu. In this case, I used it to verify that indeed the package "libcv-dev" actually contains the headers (as you wrote that you found none). It looks like it does - in "/usr/include/opencv". 

If your tutorial now states that '#include "cv.h"' is the correct way of including the header for that library, you will need to add this directory to the list of directories the compiler should look into when searching for header files. For g++, you can use the "-I" flag. So for example if you have a single-file program named "test.cpp", you can compile it using:
```

g++ -o test -I/usr/include/opencv -lcv test.cpp

```

Note that I've also added "-lcv" - This tells the linker (as I didn't add the "-c" flag to g++, compiling & linking is done in one step) to also link against that library. Try using your library without that flag. You will see that compiling will work well, but linking won't.

---

### Post by Lyon on 2009-12-07
Thank you! That was a very helpful explanation! Nowhere could I find anything that explained it like that :)

---

