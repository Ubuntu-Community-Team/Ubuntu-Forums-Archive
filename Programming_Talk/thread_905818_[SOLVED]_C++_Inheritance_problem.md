---
title: "[SOLVED] C++ Inheritance problem"
date: 2008-08-30
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-08-30
I have a large group of classes all of which have the same parent class of Base. If I include more that one child class file (Child.h), then I get a redefinition problem because all the children include the same Base.h file

how do i get around that

---

### Post by yabbadabbadont on 2008-08-30
```
#ifndef BASE_H
#define BASE_H

...  rest of bash.h code

#endif

```

---

### Post by monkeyking on 2008-08-30
You should set er preprocessor flags like

```

#ifndef _BASE_H
#define _BASE_H
#include "base.h"
#endif

```

instead of your #include "base.h".

Otherwise, use
```

#PRAGMA once

```

in your base.h file

good luck

---

### Post by StOoZ on 2008-08-31
> **monkeyking said:**
> You should set er preprocessor flags like

```

#ifndef _BASE_H
#define _BASE_H
#include "base.h"
#endif

```

instead of your #include "base.h".

Otherwise, use
```

#PRAGMA once

```

in your base.h file

good luck

what does 
```

#PRAGMA once

```
is for?

seen that couple of time in several places.

---

### Post by monkeyking on 2008-08-31
When the preprocessor reads a file that contains pragma once.
It will only be included once.
Even if it the file has been set to be included multiple times.

The use of pragmas are not recommened, since they don't conform to any standard.
But it's a nice hack if you have to add
```
#ifndef _BASE_H
#define _BASE_H
#include "base.h"
#endif
```
to the top of 20 files.

Futhermore I always add this stuff to the very top of my programs.

I don't like the way some people do, where they have en #endif,
at the very bottom of a file.


[http://en.wikipedia.org/wiki/Include_guard](http://en.wikipedia.org/wiki/Include_guard)
and
[http://en.wikipedia.org/wiki/Pragma_once](http://en.wikipedia.org/wiki/Pragma_once)

---

### Post by NovaAesa on 2008-08-31
You are better off using a macro guard rather than the #pragma once preprocessor directive. #pragma once make sure that the file that it is in is only included once in the compile, *however* it is non standard, and hence reduces code portability. EDIT: monkey king beat me to that particular point :P

You are better off using a macro guard like yabbadabbadont suggested. ie:
```

#ifndef CLASS_H
#define CLASS_H
<what was in your .h file goes here>
#endif

```

---

### Post by dribeas on 2008-08-31
> **monkeyking said:**
> 
```
#ifndef _BASE_H
#define _BASE_H
#include "base.h"
#endif
```

It is better to have include guards inside the .h than outside. Long time ago it was said that having them in the .h was slower as the compiler had to actually read the file before knowing that it had to be discarded. That is the reason that #pragma once was developed by compiler writers. The compiler knows that it must be included only once and thus will not open/read the file again. Nowadays most recent compilers [*] know about the header guard idiom and optimize the .h reading away without pragmas.

David

[*] I have not checked, but Sutter points this out in Exceptional C++.

---

