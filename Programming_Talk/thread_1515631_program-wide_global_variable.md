---
title: "program-wide global variable"
date: 2010-06-22
forum: Programming Talk
---

### Post by tbastian on 2010-06-22
I have a program split up into a large number of files, and a number of them need to access the path of the currently opened file.

Right now I have a file named 'Common.hpp' and I declare the filename.

```
static std::string log_file = "";

```

and I set it in one place in my program, but it doesn't get set in other areas. I did some debugging and found that every file apparently has their own copy of 'log_file'.

My understanding of the 'static' keyword is that its allocated once when the program runs. Apparently this isn't quite accurate... How would I do this without passing the string through a million functions (ie, how do I get a consistent view of 'log_file')? Do I have to declare the variable as 'extern' somewhere? 

Also, whats wrong with my view of 'static'?

---

### Post by johnl on 2010-06-22
A static global variable is different from a static variable inside a function or a static member function/variable.

A static global variable or a static (non-member) function means that object has *static linkage*, meaning it is only accessible to code inside the current compilation unit.  Generally this means it's visibility is at a file-level.  With your 'static string log_file', each time the header file was included in a separate file, that file got it's own, private variable named 'log_file'.

This would be the C-ish way to do what you are asking.  In C++ you might consider a singleton or some other fancy design pattern.

```

// foo.h
#ifndef _FOO_H_
#define _FOO_H_
#include <string>

// allow other files to access our variable
const std::string& get_log_file();
#endif

```

```

// foo.c
#include "foo.h"

// this is private to this file
static std::string log_file;

const std::string& get_log_file() 
{
    return log_file;
}

```

```

// test.c

#include "foo.h"

const std::string& log_file = get_log_file();

```


Alternatively, put the following in a header file:

```

extern std::string log_file;

```

And in a single .c file:
```

std::string log_file;

```

---

### Post by tbastian on 2010-06-23
Thanks alot. That was a very helpful tutorial.

---

