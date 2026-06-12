---
title: "Question about #ifndef"
date: 2010-01-02
forum: Programming Talk
---

### Post by lewisforlife on 2010-01-02
Should every C header file include:

```
#ifndef __HEADER_H__
#define __HEADER_H__

#endif
```

Also, should I put function prototypes and other header files in between also, for instance:
```

#ifndef __HEADER_H__
#define __HEADER_H__

#include <math.h>

int addition (int x, int y);

#endif
```

or should the function prototypes go outside of the #endif?  I am confused, thanks for the help.

---

### Post by lisati on 2010-01-02
It's up to you - the preprocessor facilities of C/C++ (and other languages) are a powerful tool that, if used well, make your life a lot easier.

One reason I'd do something like your second example, with the declarations in the #ifndef/#endndef block is to make sure that I do one particular set of declarations only once during the compilation of a particular file.

---

### Post by wmcbrine on 2010-01-02
> **lewisforlife said:**
> Also, should I put function prototypes and other header files in between also, for instance:
```

#ifndef __HEADER_H__
#define __HEADER_H__

#include <math.h>

int addition (int x, int y);

#endif
```Yes (assuming you change "HEADER" to the actual name, and ensure that it's a unique name). This allows the file to be included multiple times without causing problems.

But mainly this is an issue for libraries. If you *know* your header file won't be multiply included, then there's no reason to go to the trouble.

> *or should the function prototypes go outside of the #endif?*That would defeat the purpose.

---

### Post by caelestis2 on 2010-01-04
Another option is 
#pragma once 
at the top. Nonstandard but portable.

---

### Post by iharrold on 2010-01-05
Yes you should always have the guard words on header files with all your code between the guard words as shown in your second example.

How it works:

The contents of the file between the #ifndef and #endif are ignored by the compiler if "__HEADER_H__" is defined.   Thus, the first time the header file is seen (loaded) during a compilation, its contents are read and __HEADER_H__ is given a value.   Shoule compiler be presented with the header file again (i.e. from another .cpp or .hpp file including it) during compilation, the contents are ignored.  The original (1st) is used instead.  This stops the compiler from having multiple definitions of the same object.

---

### Post by dribeas on 2010-01-06
> **wmcbrine said:**
> 
But mainly this is an issue for libraries. If you *know* your header file won't be multiply included, then there's no reason to go to the trouble.


This is nonsense. If it is a header it is meant to be included from at least one other compilation unit and at one point or another you will probably end up with the header being included indirectly more than once. 

If the declarations are not to be shared, do not split into header and implementation files. If they are to be shared, add macro guards. That is a simple rule of thumb (and in many IDEs automatically implemented in the environment)

---

