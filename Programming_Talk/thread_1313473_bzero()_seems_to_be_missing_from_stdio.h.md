---
title: "bzero() seems to be missing from stdio.h"
date: 2009-11-03
forum: Programming Talk
---

### Post by Jolfulorc on 2009-11-03
Hi,

I'm designing a software which gets data from a USB port. I need to install the LibSerial library. When I launch make, I get an error. After further investigations, it turns out that something seems to be missing from stdio.h. A simple code like this :
```
#include <stdio.h>

using namespace std;

int main(){
    bzero( stuff );

}
```

gives at compilation :
> g++ -o essai essai.cc 
essai.cc: In function ‘int main()’:
essai.cc:6: error: ‘bzero’ was not declared in this scope

I'm on Ubuntu 9.10 (which is great by the way ;))... Anyone knows how to solve this ?
Cheers,
Jol
**

---

### Post by snova on 2009-11-03
> **Jolfulorc said:**
> After further investigations, it turns out that something seems to be missing from stdio.h.

Missing, or never belonged there? It has nothing to do with IO...

> I'm on Ubuntu 9.10 (which is great by the way ;))... Anyone knows how to solve this ?

By including **strings.h**, where it's located. Or alternatively by using memset() instead, since this function is deprecated (from "man bzero").

---

### Post by Jolfulorc on 2009-11-04
With <strings.h> it worked. It's weird I read a lot of stuff about bzero and stdio being related though.

Anyway, thanks!

---

