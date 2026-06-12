---
title: "C++ splittin program over multiple files problem"
date: 2011-01-19
forum: Programming Talk
---

### Post by mrkazoodle on 2011-01-19
Hi,

I'm learning how to use header files. Using code::blocks, I made a working example, but when I tried passing a parameter it stopped working and I don't understand why.

```
*******************
main.cpp:
*******************
#include <iostream>
#include "out.h"

int main()
{   float var;
    std::cin >> var;
    out::out(var);
    return 0;}

*******************
out.h:
*******************
#ifndef OUT_H
#define OUT_H

class out
{   public:
        out(float);};

#endif // OUT_H

*******************
out.cpp:
*******************
#include <iostream>
#include "out.h"

out::out(float var)
{   std::cout << var;}
```

ERRORS:
In function 'int main()':
line 7 error: conflicting declaration 'out var'
line 5 error: 'var' has a previous declaration as 'float var'

---

### Post by Zugzwang on 2011-01-19
The following line is wrong:
```

out::out(var);

```

If you want to create an instand of the "out" class using "var" as parameter to the constructor of the "out" class, do it as follows:
```

out name_of_object(var);

```

Don't forget to choose a good name for your class instance (replace "name_of_object" by whatever you like).

---

### Post by mrkazoodle on 2011-01-19
thank you very much ;)

---

