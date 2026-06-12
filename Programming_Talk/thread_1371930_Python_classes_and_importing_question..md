---
title: "Python classes and importing question."
date: 2010-01-03
forum: Programming Talk
---

### Post by caelestis2 on 2010-01-03
I'm a starting newbie with python with some experience in C++

The question: If I have a class that needs a std library module such as math, would I import it under the class definition and reference like self.math or would it be better to just import it into global namespace? How exactly does import work, and in relation to C++ do I need to worry about multiple import maths to the global namespace?

Like so:
```

class MyClass:
    import math
    def getCos(self,x):
        return self.math.cos(x)

```

Edit: Unrelated, but I find that strings being immutable is quite annoying. Is splicing strings and storing them again the only way to go?

---

### Post by OgreProgrammer on 2010-01-04
Have a read here caelestis

[http://effbot.org/zone/import-confusion.htm](http://effbot.org/zone/import-confusion.htm)

You can probably do something like 
```

import sys
if 'math' not in sys.modules:
    import math

```as well.

Isnt python awesome?

---

### Post by caelestis2 on 2010-01-04
The link you just had said that that code is what python does in the background. For the main question I am still confused, if the module is already imported into a class namespace, that means I cant import it again into global namespace?

Thanks.

Oh, one more question: I see many ways to do squaring. Such as x*x or x**2 or pow(x,2)

Which one is the best way, or are x**2 and pow(x,2) the same? The syntactic one doesn't require math but pow does.

---

### Post by OgreProgrammer on 2010-01-04
It simply replaces it near as I can tell. You dont have to worry too much.

I like to test things with the command line version of python in the terminal. Putting import math twice in a row seems to not throw any errors, so I think you are fine.

The basic math functions dont need the math module as you rightly said. You can use whichever appeals more to you. For instance, I have a friend who avoids keywords as much as possible. He would prefer x**2.

The functional ones perhaps have a tiny bit more overhead, but it shouldnt matter. You can also do some nifty tricks with them like pow(n, 1/3) for a cubic root.

---

### Post by Axos on 2010-01-04
I'm not sure what you are trying to do. Your module shouldn't be so large and contain such unrelated code that importing a module like math at the top of the file (rather than inside a class) would cause a problem for the rest of the code in the module. I recommend importing math at the top of the file. If the module contains code which is adversely affected by doing that, that code surely belongs in a different module.

"Global" just means global to the module. It doesn't affect the namespace of any other modules.

Have you been through the Python tutorial? It's really excellent. Here's a link to the discussion about scopes and namespaces:

[http://docs.python.org/3.1/tutorial/classes.html#python-scopes-and-namespaces](http://docs.python.org/3.1/tutorial/classes.html#python-scopes-and-namespaces)

---

### Post by Axos on 2010-01-04
Whoops, that's a link to the Python 3 tutorial! I sometimes get the feeling I'm the only person alive who uses Python 3. If you are using Python 2, you'll want this one: 

[http://docs.python.org/tutorial/classes.html#python-scopes-and-namespaces](http://docs.python.org/tutorial/classes.html#python-scopes-and-namespaces)

---

