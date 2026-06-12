---
title: "how to put a break point in another file in gdb"
date: 2011-01-16
forum: Programming Talk
---

### Post by karpay on 2011-01-16
Hi all!

I'm trying to debug a program which has 3 files.

There is one .h file, one .cc file and one main file.

Suppose the code is as follows:

```

//class1.h
#include "class1.h"
#include <stdio>
#include <iostream>
using namespace std;

class class1
{
   class1();
   function1();
};


```

```

//class1.cc
#include "class1.h"
#include <stdio>
#include <iostream>
using namespace std;

class1::class1()
{

}


class1::function1()
{
  [COLOR="Red"] cout << "this is class one"<< endl;[/COLOR]
}


```


```

//the main code
//main.cc
include "class1.h"

int main(int argc, char* argv[])
{
    class1 *obj1 = new class1();
    obj1->function1();
}



```

What I'm asking is how can I put a break point in the line

cout << "this is class one"<< endl;

in class1.cc. (please, check the red line above)

Any kind of help is kindly appreciated.

Regards.

---

### Post by quick-dudley on 2011-01-17
```
break class1.cc:15
```
Unless I've miscounted the line number

---

### Post by dwhitney67 on 2011-01-17
Or 
```

b class1::function1

```
If you have multiple overloaded function1() functions, then be more specific when setting the breakpoint by specifying the parameter types that the function accepts; for example:
```

b class1::function1(int)

```

Or you can list the function using the directive "list" and then set the breakpoint as quick-dudley indicated.

IMHO, interfacing with **gdb** became obsoleted with the advent of X11 for Linux.  You should use **ddd**, for it has a more intuitive interface.

---

