---
title: "global function"
date: 2010-09-23
forum: Programming Talk
---

### Post by _sluimers_ on 2010-09-23
Hi there, I have debugging errr... what's it called, a module?
Anyway, it uses a global function called int2string. The thing is, whenever another err... cpp file imports "debug.h" it start complaining about int2string not being found.
This is the error I get:

```

error: &#8216;string2chr&#8217; was not declared in this scope

```

debug.cpp
```

#include "debug.h"

string int2string(const int& number) {
   ostringstream oss;
   oss << number;
   return oss.str();
}

```

debug.h
```

#define DEBUG

#ifndef DEBUG_H
#define DEBUG_H

#include <iostream>
#include <string>
#include <sstream>
using namespace std;

#ifdef DEBUG

/* just a helper for code location */
#define PyDEBUGSTR (string("print('debug: ") + __FILE__ + ":" + int2string(__LINE__) + "')").c_str()
#define LOC cout << "debug:" << __FILE__ << ":" << __LINE__ << " ";
#define PyLOC PyRun_SimpleString(PyDEBUGSTR);

/* macro for general debug print statements. */
#define DEBUG_PRINT(text) LOC cout << text << endl;

/* macro that prints a variable name and its actual value */
#define DEBUG_VAR(text) LOC cout << (#text) << "=" << text << endl;

/* python macro that prints a variable name and its actual value */
#define DEBUG_PyRUN(text) PyLOC PyRun_SimpleString(text);

/* python macro that prints an error */
#define DEBUG_PyERR(type, text) PyLOC PyErr_SetString(type, text);

#else

/* when debug isn't defined all the macro calls do absolutely nothing for C++ debugging code and the same without helper for python debugging code */
#define DEBUG_PRINT(text)
#define DEBUG_VAR(text)
#define DEBUG_PyRUN(text)
#define DEBUG_PyERR(type, text) PyErr_SetString(type, text);

#endif /* DEBUG */
#endif /* DEBUG_H */

```

So my question is, how do I add the global function to the header file?

---

### Post by Barrucadu on 2010-09-23
Just add the function prototype to your header file:

```
string int2string(const int& number);
```

---

### Post by dwhitney67 on 2010-09-23
And remove the "using namespace std;" statement from the debug.h header file!

---

### Post by _sluimers_ on 2010-09-23
Okay thanks, that didn't work last time I tried, though I didn't omit 
using namespace std;

---

