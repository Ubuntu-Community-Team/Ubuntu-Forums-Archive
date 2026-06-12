---
title: "[SOLVED] problem with include path with g++"
date: 2008-08-24
forum: Packaging and Compiling Programs
---

### Post by lemonsf on 2008-08-24
Greetings,

wondering if anyone can help me out there.... I keep getting a g++ compilation error, and just need justification that I'm using the correct syntax for includes.

```

lemon@lemon-desktop:~/eyen$ g++ linux/clmain.cpp -o obj/main.o
linux/clmain.cpp:1:32: error: ~/eyen/src/version.h: No such file or directory
linux/clmain.cpp: In function ‘int main(int, char**)’:
linux/clmain.cpp:6: error: ‘EYEN_BUILD_NAME’ was not declared in this scope
linux/clmain.cpp:6: error: ‘EYEN_PLATFORM’ was not declared in this scope
linux/clmain.cpp:6: error: ‘EYEN_ARCHITECTURE’ was not declared in this scope
lemon@lemon-desktop:~/eyen$ ls src
architecture.h  build.h  types.h  types.h~  version.h  version.h~
lemonl@lemon-desktop:~/eyen$ cat linux/clmain.cpp
#include "~/eyen/src/version.h"
#include <iostream>

int main ( int argc, char** argv )
{
        std::cout << "eyen " << EYEN_BUILD_NAME << " " << EYEN_PLATFORM << " " << EYEN_ARCHITECTURE << '\n';
        return 0;
}

```

It says 
```

linux/clmain.cpp:1:32: error: ~/eyen/src/version.h: No such file or directory
```yet ```
lemon@lemon-desktop:~/eyen$ ls src
architecture.h  build.h  types.h  types.h~  version.h  version.h~
```

Has anybody else had problems like this. I've been developing in c++ for a number of years, but have just made the jump to linux, have noticed that g++ ( although on windows, haven't used before ) is a lot stricter about a few things, have I fallen for one of these.

Any help would be appreciated.. regards

P.S the offending code
```

#include "~/eyen/src/version.h"
#include <iostream>

int main ( int argc, char** argv )
{
        std::cout << "eyen " << EYEN_BUILD_NAME << " " << EYEN_PLATFORM << " " << EYEN_ARCHITECTURE << '\n';
        return 0;
}

```

---

### Post by lemonsf on 2008-08-24
Turns out g++ doesn't accept tilde expansion....

---

