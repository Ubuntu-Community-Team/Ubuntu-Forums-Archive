---
title: "Python importing question"
date: 2008-04-30
forum: Programming Talk
---

### Post by Minguo on 2008-04-30
So, I'm still learning python and programming and general, but I've hit a snag I don't seem to be able to figure out from using either documentation or web sources.  If anybody has any insight It would be much appreciated.

So I created a basic python module, which I've named 'main'.  It imports 4 other modules for various reasons. (1 module is full of class definitions, another has a bunch of utility functions, etc.) 

Now, In the main module, I have a variable that I need the code in one of the imported modules to be able to reference, and it is not convenient to pass the variable by a function call, I'd just like to be able to make it available to the secondary module's namespace. . . but I don't seem able to do this.

```
from main import variable_name as local_name
```

The above code placed in the secondary module seems to work, but when the script is run the 'main' module is run twice, seemingly the import call 'reinitializes' the main module, which makes it useless.

```
import main

. . ..

local_variable1  = local variable2 + main.variable_name 
```

This code doesn't work at all, the interpreter thinks that 'main' is an invalid namespace.  

I tried defining a function in the main module that returns this variable, and then importing that instead, but each time I try the interpreter says that I 'cannot import function_name'.  

Making the variable global doesn't work. (Doesn't make it available code in the secondary module.  HOw should I be going about this?

---

### Post by WW on 2008-04-30
> **Minguo said:**
> ...  If anybody has any insight It would be much appreciated.

[...]

Now, In the main module, I have a variable that I need the code in one of the imported modules to be able to reference, and it is not convenient to pass the variable by a function call, I'd just like to be able to make it available to the secondary module's namespace. . .

You asked for insight, so I hope you don't mind if I simply say that this sounds like a bad design.

Why is it "not convenient" to pass the variable to the functions that need it?

---

### Post by pmasiar on 2008-04-30
```

# main.py:
variable1 = 0

=======

# even_mainer.py

import main

localcopy = main.variable1 
main.variable1 = 42
print localcopy # prints 42, localcopy is 'alias'

```

All code in main should be in def: blocks, importing executes all code. [canonical way to write main](http://www.artima.com/weblogs/viewpost.jsp?thread=4829)

BTW you should not import main.py - it should be the main module, running all others. Even 'main' is too vague - call it what it does, even if it has the ony function defined, called main(). How you are going to remember what your program does?

---

### Post by Minguo on 2008-05-01
Thanks for the replies.  

The reason why it is inconvenient to pass the needed variable is b/c some of these secondary modules are only conditionally executing code that requires the variable, of course there isn't anything wrong with passing unneeded information, but it just . . . bugs me.   Since I've been playing with it some more, the 'inconvenience' of doing it that way is surpassed by the impossibility of doing it my way.  :)  I'm redesigning the algorithm now.

---

