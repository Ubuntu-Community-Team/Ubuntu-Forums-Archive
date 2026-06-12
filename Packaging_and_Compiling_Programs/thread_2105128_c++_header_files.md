---
title: "c++ header files"
date: 2013-01-15
forum: Packaging and Compiling Programs
---

### Post by linuxonbute on 2013-01-15
I am trying to make sense of C++ and headers.
I posted yesterday about a problem I had and the solution was that C++ headers did not include .h in them
This worked fine but i am not sure if all header files need to be like this or not. The program I have been trying to write now includes
```

#include <cstdio>
#include <ctime>
#include <cstring>  /* String function definitions */
#include <cstdlib>

#include <fcntl.h>   /* File control definitions */
#include <errno.h>   /* Error number definitions */
#include <SDL/SDL.h>
#include <sys/io.h>
#include <iostream>
using namespace std;

```
Now I can see that all the c++ ones do not have '.h' at the end but is there some list which I can refer to so for example, I could use the c++ equivalent to fcntl.h?

---

### Post by leviteo on 2013-01-16
Hey,

Look in the internet for C++ API.

As an example: [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

---

### Post by linuxonbute on 2013-01-16
> **leviteo said:**
> Hey,

Look in the internet for C++ API.

As an example: [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

Great thanks, just what I was looking for!

---

### Post by MG&amp;TL on 2013-01-16
> **linuxonbute said:**
> Great thanks, just what I was looking for!

Any that you don't find in the C++ standard library will *usually* have ".h" appended to them, or, more rarely, ".hpp". :)

---

