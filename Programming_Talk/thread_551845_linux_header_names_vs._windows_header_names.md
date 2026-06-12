---
title: "linux header names vs. windows header names"
date: 2007-09-15
forum: Programming Talk
---

### Post by Marcipicus on 2007-09-15
Hi I am taking a course in c++ programming in university (Data structures and algorithms) and we are making basic programs for a windows console environment. They gave us a "standardstuff.h" file for visual C++ and borland c++ so they wouldn't have to change the header files when marking in different development environments.

So how would I go about making a "stdstuff.h" header file so I could develop my assignments in a linux environment?

stdstufff.h is 

// we only want this stuff if stdstuff has not previously been included
// (i.e. if "stdstuff_included" has not been defined)
#ifndef stdstuff_included
#define stdstuff_included

// Header file for Visual C++ 6.0 environment with "pause".

#include <iostream>
#include <fstream>
#include <strstream>
#include <iomanip>
#include <stdexcept>
#include <limits.h>
#include <string>
#include <math.h>

#include <process.h>
#include <ctype.h>

#include <conio.h>

using namespace std;

#define pause() // dummy out pause function

#define clearScreen() system("cls")

#endif

---

### Post by t3hi3x on 2007-09-15
> **Marcipicus said:**
> 
#include <iostream>
#include <fstream>
#include <strstream>
#include <iomanip>
#include <stdexcept>
#include <limits.h>
#include <string>
#include <math.h>


these are all the same as far as i know.

---

### Post by slavik on 2007-09-15
you don't need that header file, especially since it has using namespace in there ...

everything else should be installed with build-essential

---

### Post by dwhitney67 on 2007-09-15
You can also insert preprocessor statements into your code such as:

#ifdef WIN32
#include <MSstuff.h>
#endif

I can't recall if WIN32 is available for "free" (under MS) or if you need to compile with a -DWIN32 preprocessor option.

---

### Post by Marcipicus on 2007-09-15
Thanks for the help, I need to send the source code so i don't have to worry about compiling the programs for windows.

---

### Post by dwhitney67 on 2007-09-15
Btw, you should avoid declaring a "using namespace" in a header file.  If you require the use of a namespace, insert the appropriate "using" statement in the implementation file (.cpp) after all header files have been included.

Never declare a "using namespace" before including header files.

---

### Post by ryno519 on 2007-09-15
> **slavik said:**
> you don't need that header file, especially since it has using namespace in there ...

everything else should be installed with build-essential

Yes, get rid of that using namespace and put it with the implementation.

Also, you have a couple of deprecated headers there. Use 

#include <cmath> //instead of math.h
#include <climits> //instead of limits.h
#include <ctype> //instead of ctype.h

I wouldn't use conio.h at all. It's not standard C or C++ and is not guaranteed to work with all compilers. Just use iostream objects instead. For pausing, wait for the input of a character, for clearing the screen, output 50 new lines.

---

### Post by ryno519 on 2007-09-15
> **dwhitney67 said:**
> You can also insert preprocessor statements into your code such as:

#ifdef WIN32
#include <MSstuff.h>
#endif

I can't recall if WIN32 is available for "free" (under MS) or if you need to compile with a -DWIN32 preprocessor option.

I believe you would have to add the preprocessor option unless you know your compiler specifically enables it by default (Visual C++ for instance).

Visual C++ will include stdafx.h in your projects which will (among other things) expose those definitions automatically.

Edit: Not 100% sure on this, but to extend that I believe the GNU compilation identifier is __GNUC__. So if you wanted to, you could do something like the following, to extend dwhitney's code.

```

#if defined(WIN32)
    #include "WinStuff.hpp"
#elif defined(__GNUC__)
    #include "GnuStuff.hpp"
#endif

```

---

