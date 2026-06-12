---
title: "C++ confusion about header files"
date: 2007-04-29
forum: Programming Talk
---

### Post by dbd on 2007-04-29
Hi,

Recently I've begun to suspect that I don't really understand the details of what happens when you include a header file, so I did some googling around and failed to find the thorough explanation of headers that told me quite what I felt I needed to know. 
However, I found [this web page]("http://www.topology.org/linux/include.html") which served to increase my confusion :)

Specifically it made this claim:
> Non-top-down header file inclusion order hides importations into header files. For example, **if A.c imports B.h then C.h, the definitions in B.h are exported to C.h.** If C.h uses these services, then this would be a hidden importation unless C.h explicitly includes B.h or else includes B.h via some other explicit inclusion into C.h. 

Now suppose the order of inclusion in A.c is changed. Then the services provided to C.h will be removed, and the code will not compile because the definitions which were required by C.h are no longer provided through their inclusion within A.c. The consequence in this case is that a change of inclusion order yields uncompilable code.

Huh? Surely if C.h itself does not include B.h (or include a file which includes B.h) then it won't be able to use anything from B.h. Why would what A.c includes make any difference to C.h?

I think I'm missing something here, anyone want to clear up my confusion?

Thanks

---

### Post by hyperair on 2007-04-29
This is what happens. Let's say you have files A.h, B.h and C.h like this:

A.h:
```

#include "B.h"
#include "C.h'

```

B.h:
```

/* code in B */

```

C.h:
```

/* code in C */

```

and finally a C++ source file to make things clearer:

source.cpp:
```

#include "A.h"
int main()
{
return 0;
}

```

What ultimately is processed by the compiler will look like this (in the specific order):
```

/*code in B*/
/*code in C*/
int main()
{
return 0;
}

```

So basically when you run an #include directive, the preprocessor just takes the entire file specified, and dumps it into the code where the #include directive was located.

Hope this helps.

---

### Post by dbd on 2007-04-29
Thanks, that's exactly what I needed to know, it all make sense now :popcorn:

---

