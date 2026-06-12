---
title: "LPDWORD and C++"
date: 2009-06-25
forum: Programming Talk
---

### Post by wbest on 2009-06-25
So, I have a program that was in Windows and I have to make work on Linux.
Now, it contains a reference to LPDWORD, which it says is not defined in the scope.  Indeed, I cannot find it anywhere defined, either in the header files or the program itself.  In fact, the only place it seems to exist in any form is in this one line in this one file.
However, I did comment out windows.h, but with the research I have done, I cannot confirm as to whether it is in windows.h.
 
Granted, LPDWORD may be specialized to the program I am working with, but in the event that it is not, I want to figure out how to fix this error.
 
Any advice?

---

### Post by dwhitney67 on 2009-06-25
I came across this with a Google search...
```

typedef unsigned long DWORD;
typedef DWORD* LPDWORD;

```

So in your code, just replace "LDPWORD" with "unsigned long*".

---

### Post by Habbit on 2009-06-25
That might not do what the OP wants, since in Windows code, "long" is 32 bits even in 64-bit machines, whereas in the wide *nix world that is not guaranteed. Porting an application is not as easy as find & replace (though if all coders were nice, it would be). Most likely you are using Windows APIs and you'll have to either find some equivalent POSIX/Linux/whatever call or use winelib. This last option might seem dirty, but it means you can be up and running fast, then have all the time in the world to port your application in The Right Way (tm). IIrc, when Apple moved from the M68K to the PPC, big parts of the OS ran on a 68K emulator until they were finally able to port all of it.

---

### Post by Zugzwang on 2009-06-26
> **Habbit said:**
> That might not do what the OP wants, since in Windows code, "long" is 32 bits even in 64-bit machines, whereas in the wide *nix world that is not guaranteed. 

No problem. Then you can adapt dwitney's example to:
```

#include <stdint.h>

typedef uint32_t DWORD;
typedef DWORD* LPDWORD;

```

---

### Post by wbest on 2009-06-26
Okay, I think that worked.
I don't get the error anymore, and I don't get any new errors...so...its cool I guess.

---

