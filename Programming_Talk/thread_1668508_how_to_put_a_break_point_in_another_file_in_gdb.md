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

### Post by karpay on 2011-01-16
Sorry, accidentially i posted the same thread twice.

Can you please delete one of the threads? Cause I do not know how to delete my thread.

Regards...

---

### Post by MadCow108 on 2011-01-16
don't worry about the double post. the forum currently has some performance problems so double posts are quite common ;)

first your file has to built with debug information (-g flag in gcc)
then you can break into files by using this syntax:
break filename:linenumber
e.g.
break class1.cc:19

you should have tab completion if the debugger knows about the file

If it does not add the folder where it is located to its search list with dir:
dir(/path/to/file/folder/)

---

### Post by karpay on 2011-01-19
Dear Mad Cow,

Thank you for the reply :)

I worked :)

Best regards..

---

### Post by Simian Man on 2011-01-19
While MadCow's suggestion does work, you can also just do:
```

(gdb) break class1::function1

```
This way you don't have to be constantly checking what line numbers functions are on.

Your code also has quite a few errors, but I guess this is just copy/paste error :).

---

### Post by psusi on 2011-01-19
Also you can run gdb under emacs and just click the margin of the line to set a breakpoint there.  It also opens the file and takes you to the line when you hit a breakpoint.

---

