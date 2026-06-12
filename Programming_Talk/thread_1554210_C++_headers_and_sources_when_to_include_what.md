---
title: "C++ headers and sources when to include what"
date: 2010-08-16
forum: Programming Talk
---

### Post by EMR on 2010-08-16
Okay, so lets say you have three source files, A, B, and C.

A is your main file, and it needs classes from B and C.
B and C are inter dependent.

At some point, before any source files are compiled, A.h, B.h, and C.h need to be included, but when do people usually include source files?

Would one simply put at the beginning of A.cpp

#include A.h
#include B.h
#include C.h
#include B.cpp
#include C.cpp

or do you include the headers from the sources, or include the sources from the headers or what?

Whats the convention?

---

### Post by EMR on 2010-08-16
Okay, so you don't use #include for source files?  Because arbitrary rule says you don't?  Well, I guess it would be:

at the beginning of each:
#include A.h
#include B.h
#include C.h

Thoughts?

---

### Post by dwhitney67 on 2010-08-16
Say 3 classes:  A, B, C.

Then A.h in A.cpp; B.h in B.cpp; and finally C.h in C.cpp.

In module that defines main(), include which header file is needed (note this may not be each of the aforementioned .h files).

If any of the .h files is dependent on another, then choose whether to include that .h file or use a forward-dependency (Google is your friend if you don't understand the latter).

Otherwise, if you require a .h in any of the .cpp, include it.


P.S.  The ordering of the include files can be relevant!  Personally, I always include first the header file for the module I'm implementing; then comes secondary project header files.  Finally, system headers files (ie iostream, string, etc).

P.S. #2  Never put a "using namespace" directive in a .h file.  (once again, Google for more information if you are in need of more info).

---

### Post by aatwo on 2010-08-16
> **EMR said:**
> Okay, so lets say you have three source files, A, B, and C.

A is your main file, and it needs classes from B and C.
B and C are inter dependent.

At some point, before any source files are compiled, A.h, B.h, and C.h need to be included, but when do people usually include source files?

Would one simply put at the beginning of A.cpp

#include A.h
#include B.h
#include C.h
#include B.cpp
#include C.cpp

or do you include the headers from the sources, or include the sources from the headers or what?

Whats the convention?

Hi. Hope this helps:

Usually, and in a lot of code I have seen people split their code between header files and cpp files. Usually (in my experience) header files are used to list all the includes, variable declarations and function declarations, while the cpp files are generally used for function definitions, and variable definitions (usually in the constructor).

So in your case the files B.h and C.h would be included in A.h, usually right at the top, but just before the macro definition.

In this case your A.h file might look like this...

```

// This is in A.h
#ifndef _A_H
#define _A_H

#include "B.h"
#include "C.h"

```

I do believe includes can be placed anywhere though, as long as they are not in a function and they come before their first use, though that might be wrong. They certainly can be placed in a cpp file though. I have seen programs with includes mixed between both the header files and cpp files, but that's just messy! :P

---

### Post by Lootbox on 2010-08-16
Also, be sure to use an include guard in your .h files if a bunch of them are including each other:
```
#ifndef _A_H
#define _A_H

// stuff

#endif
```

Or, slightly easier:

```
#pragma once

// stuff
```

That avoids issues with re-definitions.

---

