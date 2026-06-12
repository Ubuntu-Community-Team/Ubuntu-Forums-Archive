---
title: "C++ header include order"
date: 2011-12-18
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2011-12-18
Hi

is there some rule that define in what order the header should be included in C++ program?

I ask this because I have one strange problem:
```

#include "download.h"
#include "compare.h"

#include <iostream>
**#include <cstdlib>**

int main(){

return 0;
}

``` 
the download.h and compare.h declare two classes

this won't compile complaining about this:
```

/usr/include/stdlib.h|351|error: ‘int32_t’ does not name a type|
/usr/include/stdlib.h|352|error: ‘int32_t’ does not name a type|
/usr/include/stdlib.h|353|error: ‘int32_t’ does not name a type|
/usr/include/stdlib.h|357|error: ‘int32_t’ does not name a type|
/usr/include/stdlib.h|361|error: ‘int32_t’ has not been declared|
||=== Build finished: 5 errors, 0 warnings ===|

```

however this compile fine:
```

**#include <cstdlib>**

#include "download.h"
#include "compare.h"

#include <iostream>


int main(){

return 0;
}

```
  
very strange

---

### Post by jake.anq on 2011-12-18
Hi

#include statements are interpreted by the C preprocessor  as saying "Replace this marker with the contents of the file named".

Example:
```
//main.cpp
#include "MyHeader.h"
//Use code from the header here
//...
```
```
//MyHeader.h
class t {
//...
};

```

When the preprocessor looks at this code, it will replace the #include directive:
```
//main.cpp
//MyHeader.h
class t {
//...
};
//Use code from the header here
//...
```

This is the code that is given to the compiler.

The compiler will then see this problem in your code:

```

int32_t var; //This is an error

// int32_t defined here.

int32_t NotError; //int32_t has been defined now, so no error produced

```

The compiler will report an error as the variable type has not been defined when it looks at the first line. The compiler then sees the definition of that type and when it gets to the last line, it knows what an int32_t is.

As a result, if header A depends on code/macros from header B, header B should be included first.  If there are no dependencies, the headers can be included in any order.

Hope this is of some help.

---

### Post by ofnuts on 2011-12-18
> **jake.anq said:**
> Hi

#include statements are interpreted by the C preprocessor  as saying "Replace this marker with the contents of the file named".

Example:
```
//main.cpp
#include "MyHeader.h"
//Use code from the header here
//...
``````
//MyHeader.h
class t {
//...
};

```When the preprocessor looks at this code, it will replace the #include directive:
```
//main.cpp
//MyHeader.h
class t {
//...
};
//Use code from the header here
//...
```This is the code that is given to the compiler.

The compiler will then see this problem in your code:

```

int32_t var; //This is an error

// int32_t defined here.

int32_t NotError; //int32_t has been defined now, so no error produced

```The compiler will report an error as the variable type has not been defined when it looks at the first line. The compiler then sees the definition of that type and when it gets to the last line, it knows what an int32_t is.

As a result, if header A depends on code/macros from header B, header B should be included first.  If there are no dependencies, the headers can be included in any order.

Hope this is of some help.
Actually the usual technique is that each of your headers includes the standard headers it needs, so i A depends on headers/macros defined in B, it should include B. The standard headers have a "protection" against duplicate use so they can be included multiple times. It's a good idea to write your own headers in the same way, typically:
```

#ifndef _HEADERNAME_H
#define _HEADERNAME_H

// declarations go here

#endif

```

---

### Post by jake.anq on 2011-12-18
> **ofnuts said:**
> Actually the usual technique is that each of your headers includes the standard headers it needs, so i A depends on headers/macros defined in B, it should include B. The standard headers have a "protection" against duplicate use so they can be included multiple times. It's a good idea to write your own headers in the same way, typically:
```

#ifndef _HEADERNAME_H
#define _HEADERNAME_H

// declarations go here

#endif

```
I totally agree with you.  In the example I was attempting to show an explanation of the problem as opposed to the ideal solution. (If that makes any sense at all:))

---

### Post by nvteighen on 2011-12-19
OK, the problem is that your custom headers are using something from cstdlib.

The best way to deal with this is the following: 

1) Always #include everything that's needed in the header, even if you know that those headers will be #included from somewhere else. This not only makes your headers be able to be used in any order, but it also serves as some kind of documentation.

2) Use guards, as already shown.

I hate the preprocessor... :-\

---

### Post by Mr.Pytagoras on 2011-12-19
Thank you

 It was the problem as nvteighen said.

---

### Post by dwhitney67 on 2011-12-19
> **Mr.Pytagoras said:**
> Thank you

 It was the problem as nvteighen said.

You should include **cstdint **within your custom header file, not **cstdlib**.  cstdint defines, as typedefs, types such as int32_t.

---

