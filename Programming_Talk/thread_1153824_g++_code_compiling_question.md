---
title: "g++ code compiling question"
date: 2009-05-09
forum: Programming Talk
---

### Post by Lampi on 2009-05-09
Can somebody explain to me this behaviour of the g++ compiler?

```
lampi@kubuntujaunty:~/temp$ cat hello.cpp
// sna@reteam.org  - 6th of April 2005


#include <cstdio>
#include <iostream>
#include <memory>

using namespace std;


int main(int argc, char **argv)
{
 cout << "Hello" << endl;
#if 0
 unsigned char *wandData = (unsigned char *) malloc(100);
 free(wandData);
#endif
 return 0;
}
```
compiles fine using g++ (Ubuntu 4.3.3-5ubuntu4) 4.3.3

but changing **#if 0 to #if 1** and compiling again will result in:

> hello.cpp: In function »int main(int, char**)«:
hello.cpp:15: Error: »malloc« not defined in this scope
hello.cpp:16: Error: »free« not defined in this scope

OS is Kubuntu Jaunty, kernel 2.6.28-11-generic, headers and build-essential installed

thanks!

---

### Post by smudi on 2009-05-09
As a rule of thumb, if using c++ code you should not use malloc/free but new/delete

---

### Post by dwhitney67 on 2009-05-09
As a rule of thumb, one should reference the man-page for any C-library function that they are (apparently) unfamiliar with.

If you reference the man-page for either malloc() or free(), you will notice that you need to include <stdlib.h>; for C++, the preferred include file is <cstdlib>.

Unless you have zero desires to become a good C++ programmer, as smudi pointed out, you should avoid these functions; use 'new' and 'delete' instead.

---

### Post by Lampi on 2009-05-09
thanks dwhitney67, #include <cstdlib> makes it compile fine :)

---

