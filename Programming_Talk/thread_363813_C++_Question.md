---
title: "C++ Question"
date: 2007-02-17
forum: Programming Talk
---

### Post by rekahsoft on 2007-02-17
Hi all, i have been learning C++ and have come upon a little hold up...I am currently learning how C++ implements object oriented programming. I am getting a error saying that i redefined the class in the header when i did not. Here is the exact error:```
Base.h:5: error: redefinition of 'class Base'
Base.h:5: error: previous definition of 'class Base'
```Here is the code from Base.h:```
#ifndef __BASE_H

#include <iostream>

class Base {
     public:
          void test();
};
#endif
```And not the code from Child.h:```
#ifndef __CHILD_H

#include "Base.h"
#include <iostream>

class Child : public Base {
     public:
          void test();
};
#endif
```And now the code from Base.cc:```
#include "Base.h"
using std::cout;
using std::endl;
void Base::test() {
     cout << "Base" << endl;
}
```And finally the code from Child.cc:```
#include "Child.h"
using std::cout;
using std::endl;
void Child::test() {
     cout << "Child" << endl;
}
```Now my question is: **Why am i getting an error saying that i redefine the class Base when i do clearly not and the headers have header gaurds?**

---

### Post by lnostdal on 2007-02-17
your include-guards are wrong ... [http://en.wikipedia.org/wiki/Include_guard](http://en.wikipedia.org/wiki/Include_guard)  (#define-part is missing)

---

### Post by hod139 on 2007-02-17
With newer versions of GCC, you can use the non-standard 
```

#pragma once

```directive instead of the standard include-guard method.  It is easier to use, just add that line at the top of your header.

---

### Post by rekahsoft on 2007-02-17
> **lnostdal said:**
> your include-guards are wrong ... [http://en.wikipedia.org/wiki/Include_guard](http://en.wikipedia.org/wiki/Include_guard)  (#define-part is missing)

oops, thanks for the help :D

---

