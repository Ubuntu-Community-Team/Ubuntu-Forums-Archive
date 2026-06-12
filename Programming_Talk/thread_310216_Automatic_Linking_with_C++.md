---
title: "Automatic Linking with C++"
date: 2006-11-30
forum: Programming Talk
---

### Post by cyberslayer on 2006-11-30
How can I create a library that will link in automatically?  I want to be able to write this:

---main.cpp file---

#include <library.h>

int main()

{

    // do stuff with library

}

--end of file---

and have my IDE (KDevelop) link in library.a when the linker runs.  I want to do this without adding any code to main.cpp but library.h can be changed to do this.  Also, how would I set things up if I wanted to use a .so file at runtime instead of using a statically linked library?  I know where to put library.h and how to create library.a and library.so.  I am using Ubuntu 6.10 with KDevelop (which is using gcc to compile everything).

Thanks

---

