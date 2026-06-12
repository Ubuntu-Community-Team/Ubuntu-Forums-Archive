---
title: "g++ compiler error on iostream method .flags()"
date: 2007-04-12
forum: Programming Talk
---

### Post by SadaraX on 2007-04-12
EDIT: I found a solution to my problem. 

Hello, I'm trying to compile some code that uses a C++ ostream method called .flags(). 

This is a simple version of what the code is doing, and where the problem occurs.

```

#include <iostream>
#include <iomanip>
long originalformat = output_stream.flags(); // saves original format
// ...various other code
output_stream.flags(originalformat); // reset flags

```

The error happens on the last line where I try to set the output_stream's flags to the original value. I am using G++ version 4.1.2. Here is the compiler output error:

error: invalid conversion from 'long int' to 'std::_Ios_Fmtflags'
error: initializing argument 1 of 'std::_Ios_Fmtflags std::ios_base::flags(std::_Ios
_Fmtflags)'

SOLUTION: The code be using 'ios_base::fmtflags' instead of 'long'.

---

