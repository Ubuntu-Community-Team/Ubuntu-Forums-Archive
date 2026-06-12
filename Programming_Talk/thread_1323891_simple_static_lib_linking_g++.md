---
title: "simple static lib linking g++"
date: 2009-11-12
forum: Programming Talk
---

### Post by lemonsf on 2009-11-12
Hello,

I have a very simple static lib linking problem, g++ doesn't seem to find the static lib that I want to link, but I'm not too sure what I'm doing wrong. Its been a while since I developed in nix, and can't remember having this problem before. Any help would be appreciated..

Here are the three source files I am using...

staticlib.h
```

#ifndef STATICLIB_INCLUDE
#define STATICLIB_INCLUDE

int staticFunc( int );

#endif
```

staticlib.cpp
```

#include "staticlib.h"

int staticFunc( int val )
{
return ++val;
}
```

main.cpp
```

#include "staticlib.h"
#include <iostream>

int main( int argc, char** argv )
{
std::cout << "result = " << staticFunc(1) << '\n';
return 0;
}

```

so to compile staticlib.cpp....
```

g++ -c staticlib.cpp -o staticlib.o
ar -rv libstat.a staticlib.o
```

but then when I compile main.cpp, linking to the lib
```

g++ main.cpp -lstat -o main

/usr/bin/ld: cannot find -lstat
collect2: ld returned 1 exit status
```

Bit of a loss here...

Many thanks in Advance

---

### Post by dwhitney67 on 2009-11-12
Assuming all your code and static-lib are in the same directory, you need to tell g++ where the static-lib is located at using the -L option.

For example:
```

g++ main.cpp -L./ -lstat -o main

```
If the library had been in a different directory, then the path to that directory would be needed.

P.S.  Nice post... all of the details were there.  We do not see that too often here on the forums.

---

### Post by lemonsf on 2009-11-12
Birlliant dwhitney67, exactly what I needed!

Thanks for the 'P.S' Since I'm asking for help, no need to waste your time time trying to second guess what I'm trying to do.

Thanks again.

---

