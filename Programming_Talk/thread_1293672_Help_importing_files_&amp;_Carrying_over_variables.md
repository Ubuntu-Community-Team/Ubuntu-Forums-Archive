---
title: "Help importing files &amp; Carrying over variables"
date: 2009-10-17
forum: Programming Talk
---

### Post by Pyro.699 on 2009-10-17
Hello,

The only reason i really require this is to make my life as a programmer much more efficient. I currently have a script which preforms several (42) tasks based on a 24 hour calendar. These tasks are preformed every day at exactly the same time; there is a function defined for each individual task. Now that has created quite the lengthy program; it is currently 4436 lines long and very very messy. Here is what i hope to achieve in the end.

I will have my main "Runner Program" which we can define ***main.py***
Then there is a folder called ***./functions/*** which contains 42 individual python files
Within each python file (located in ***./functions/***) the functions which previously resided in ***main.py*** will be the code that was in the function corresponding with the file name (minus the ***def functionOne([args]):***)
Within ***main.py*** i can run something like **functionOne** and it will run the code that is located within ***./functions/functionOne.py***

Here is what i have done sofar:

***./main.py***
[php]
import imp
funcs = ['functionOne']

for func in funcs:
    exec("def %s(): return imp.load_source('', './functions/%s.py')"%(func,func))

#Predefine a variable to be used  by other functions
test = 2
#When its time to execute
functionOne()
[/php]

***./functions/functionOne.py***
[php]
'''

Some information about this script

'''

print 1
print test
[/php]

The error is that the variable defined in ***./main.py*** is not carried over when we import ***./functions/functionOne.py***. The types of variables that will be carried over in the actual program will actually be classes, objects, functions and other methods.

I really hope i can get this to work; it will make my work much much easier. If you need more clarification i can do my best to try to elaborate a bit more.

Thanks
~Cody Woolaver

---

### Post by Bachstelze on 2009-10-17
Put a file named __init__.py in your functions dir and you can import it as a module.

```
firas@itsuki ~ % cat main.py 
from functions import *
n = 2
hello.hello(2)

firas@itsuki ~ % cat functions/__init__.py
import hello

firas@itsuki ~ % cat functions/hello.py
def hello(n) :
        print "Hello, the number is %s!" % n

firas@itsuki ~ % python main.py 
Hello, the number is 2!

```

---

### Post by Bachstelze on 2009-10-17
Also, about variables: if a variable is defined outside a function, you can't use it inside it. You have to make it global (bad, since it will pollute your namespace), or pass it as a parameter to the function, as I did.

---

### Post by Pyro.699 on 2009-10-17
Well, there are too many variables, classes and such to pass them as arguments. What if i created a dictionary containing all of the variables i wanted to carry over, and then parsed that into the globals.

---

### Post by Bachstelze on 2009-10-17
Well, it depends wht your functions do. How about passing the dictionary as argument?

---

### Post by Pyro.699 on 2009-10-17
Well, using your example i would prefer not to use ***hello.hello(n)*** but rather just **hello(n)**

Thanks
~Cody

---

### Post by Bachstelze on 2009-10-17
> **Pyro.699 said:**
> Well, using your example i would prefer not to use ***hello.hello(n)*** but rather just **hello(n)**

Thanks
~Cody

In __init__.py, replace [font=monospace]import hello[/font] with [font=monospace]from hello import *[/font].

---

### Post by Pyro.699 on 2009-10-17
Alright Im almost there.

I needed to convert the dictionary back into variables for the program to use. Heres what i wrote:
[php]
from types import *

def StartUp(dict):
    for item in dict:
        if type(dict[item]) is StringType:
            exec("global %s; %s = '%s'"%(item,item,dict[item]))
        else:
            exec("global %s; %s = %s"%(item,item,dict[item]))
    del item, dict
[/php]

That works fine for strings and numbers but when it comes to an object it fails. I know that it is because i am using ***%s*** but there is no ***%<object>*** so does anyone have any clue how i can parse an object back to a variable.

Thanks
~Cody

---

### Post by A_Fiachra on 2009-10-17
Style-wise, you might want to use the import method like:

from Package import class1, class2, class 3

from Foo import * works, but you pull in EVERYTHING in the Foo namespace -- that'd be an OO blunder .. or at least not in good OO style.

From the other side -- write your packages to ONLY expose full classes which hide their internals and use accesors and mutators to get/set object data.


It's really so easy with Python, it's worth using good OO style.

Cheers!

---

### Post by Bachstelze on 2009-10-17
I still don't get what you want to do here. Why not just pass the dict to te functions? Global variables are bad, and exec() is even worse.

---

### Post by Pyro.699 on 2009-10-17
Thanks A_Fiachra,

I changed the __init__ to only ***import init, run***

Regarding using classes, i would like to keep the clutter of the script (such as creating a class for each one) down to a minimum. My original goal was to just have python files containing code and to run them from that. But i have setup a ***run*** function which now contains the code to run. Creating a class for each object would be a bit much.

I know it doesn't matter but there are actually 56 functions ;) not 42 xD

Thanks
~Cody

---

### Post by Pyro.699 on 2009-10-17
If i passed a dict and used them directly from that i would have to rewrite all of the code that is already there. For instance i have a ***p*** class which is my output class. If i was to run it from the dict i would have to replace the ***p*** with ***dict['p']*** which i would prefer to avoid.

---

### Post by Bachstelze on 2009-10-17
> **Pyro.699 said:**
> If i passed a dict and used them directly from that i would have to rewrite all of the code that is already there. For instance i have a ***p*** class which is my output class. If i was to run it from the dict i would have to replace the ***p*** with ***dict['p']*** which i would prefer to avoid.

sed much?

Anyway, I guess what you want is

exec("global %s; %s = dict['%s']" % (item, item, item))

---

