---
title: "gtkmvc and python modules, where the hell do I put this stuff?"
date: 2009-10-12
forum: Programming Talk
---

### Post by J V on 2009-10-12
Where the hell do I put my classes? From what I can see to get a working app I would need to write the entire program in a single file, how do I put models in one module, ctrlrs in another and views in the last?

Everything I know about computers says its impossible :/

Am I just supposed to "from 1, 2, 3 import *"?

---

### Post by Tony Flury on 2009-10-12
From what I know it is a bad, bad idea to use 
```

from <x> import *

```
As you get everything from x straight into your global naming scope.

It is considered better to use 
```

from <x> import <y>
[/CODE[
at least now you only get <y> in your global name scope

or you can use 
[CODE] import <x> 
``` 
Which means you get everything in <x> so long as you qualify it.

Note : <x> is a module and <y> is a class defined within the module.

And if everything you know about computers is telling you it is impossible to split your classes up into different python files - then you are missing something fundamental about computers or python.

The import command in python is designed to enable you to do exactly what you want, to define different classes in different modules and for your application to only use what is actually needed.

What makes you think it is impossible ? Maybe there is something that i am missing about the problem you are having - if you reply and explain (with an example of the code you are having trouble with, then we will be better placed to help.

---

### Post by J V on 2009-10-12
Well, in an application (mvc) where controllers modules and views are sent to seperate files, how does one reference the other?

How would a controller connect to the modules and views which are both in different files after they have already been referenced into main?

Do I have to stick "from x import y" above every single file?

---

### Post by snova on 2009-10-12
> **J V said:**
> Do I have to stick "from x import y" above every single file?

If every single file needs access to y, then yes.

---

### Post by J V on 2009-10-12
I mean like this:
(The point of interest being the references to other .py files in the program, isn't there a way to make all of the files import automatically?)

```
# ctrl.py
from gtkmvc import controller
from views import myView # point of interest

class controling(controller):
    #Bla bla bla...
``````
# views.py
from gtkmvc import View
from ctrl import controling # point of interest

class myView(View):
    # bla bla bla...
```

---

### Post by snova on 2009-10-12
> **J V said:**
> I mean like this:
(The point of interest being the references to other .py files in the program, isn't there a way to make all of the files import automatically?)

No.

> ```
# ctrl.py
from gtkmvc import controller
from views import myView # point of interest

class controling(controller):
    #Bla bla bla...
``````
# views.py
from gtkmvc import View
from ctrl import controling # point of interest

class myView(View):
    # bla bla bla...
```

That would work fine.

I should clarify that unless you are creating instances of the class (or otherwise manipulating *the class itself*) you don't need to import its module. If you know what kind of object is being passed to methods of controling/myView, then you can use them as you like.

---

### Post by J V on 2009-10-12
Ahh so I should use #1 rather than #2?

```
class x:
    def breakY(self,toBreak):
        toBreak.broken = True
# main.py
x = x()
y = y()
x.breakY(y)
``````
class x:
    def breakY(self):
        y.broken = True
# main.py
x = x()
y = y()
x.breakY()
```Clumsy example, but I should pass the object to change from the main parent rather than open straight from the class yes?

---

### Post by Can+~ on 2009-10-12
You know, I always have that doubt when working with classes, something like "How can I separate two modules, but I know that both classes will be working together, why do I have two classes in the first place".

But then I think "A class should be detached from any interaction with another class, therefore, only when I'm gonna implement them into something that actually does something, I should connect them".

So I "direct" my OO-ness into having methods which act like "plug-in" to other classes that I defined, so I can bind them together. And due to the ample polymorphism of python, you could do this with a class that "looks like" another and bind them together for diverse results.

Answering the previous question, a simple way to solve your problem, would be to make a package and use intra-reference:

[http://docs.python.org/tutorial/modules.html#intra-package-references](http://docs.python.org/tutorial/modules.html#intra-package-references)

---

### Post by snova on 2009-10-12
> **J V said:**
> Ahh so I should use #1 rather than #2?

```
class x:
    def breakY(self,toBreak):
        toBreak.broken = True
# main.py
x = x()
y = y()
x.breakY(y)
``````
class x:
    def breakY(self):
        y.broken = True
# main.py
x = x()
y = y()
x.breakY()
```Clumsy example, but I should pass the object to change from the main parent rather than open straight from the class yes?

Yes, especially as #2 is using global variables (try to avoid those...).

I might also point out that by naming your class ("x") the same as the variable ("x"), you're shadowing the class and making it entirely unavailable from the rest of that module. As a general convention, classes are capitalized.

---

### Post by J V on 2009-10-13
ok, thanks for the help!

(but can+~, you think deep thoughts :) )

[SOLVED]

---

