---
title: "Python Classes and Importing"
date: 2008-04-05
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-04-05
In Python i wish to make a class uses an external library


I will give a Java example because thats what i know best, I wish to copy this into Python:

```

package test;

import java.awt.*;

public class test {
[INDENT]public test(String msg) {
}[/INDENT]}

```

Basically in python i want to import an external package like "java.awt"

---

### Post by Can+~ on 2008-04-05
When importing with python, you can either:

[PHP]
import external_library

external_library.doSomething()
a = external_library.newClass()
...
[/PHP]

That makes all the globals (if any), functions and classes on the library be referenceable prepending external_library.

[PHP]
from external_library import *

doSomething()
a = newClass()
[/PHP]

That will load everything in the current namespace, which is a bad idea, unless you will use ONLY those functions. This is useful, if you want to build a calculator, and import everything on math library, so you can use PI and all those fancy functions without prepending math. Or importing openGL libraries, etc. You can also import one element:

[PHP]
from external_library import doSomething

doSomething()
[/PHP]

Which is a tad safer than the one before.

---

### Post by Mr.Macdonald on 2008-04-05
Yes but inside a class

> class test:
[INDENT]def __init__:
[INDENT]dosomething() #that requires an import Where do you put it[/INDENT][/INDENT]

also in a CGI script how do you secretly submit a variable
I know that you can use a form to submit but i don't want the source to display what that form's value is

---

### Post by Quikee on 2008-04-06
Where do you "declare" imports in Java? It's the same in Python. 
[PHP]
import sys

class Test:
    def __init__():
        print sys.version
[/PHP]

---

### Post by smartbei on 2008-04-06
About submitting variables - If the user is submitting it, they can see it. I think what you are looking for is sessions - see [http://jonpy.sourceforge.net/](http://jonpy.sourceforge.net/) for an example (see the session module).

---

### Post by SOULRiDER on 2008-04-06
> **Mr.Macdonald said:**
> In Python i wish to make a class uses an external library


I will give a Java example because thats what i know best, I wish to copy this into Python:

```

package test;

import java.awt.*;

public class test {
[INDENT]public test(String msg) {
}[/INDENT]}

```

Basically in python i want to import an external package like "java.awt"


My solution would be:
```
import whatever

class Test

    def __init__(self, message):
        pass

```

Replace pass with whatever you want the constructor to do.

---

