---
title: "Simple python"
date: 2006-06-05
forum: Programming Talk
---

### Post by Ubuntuud on 2006-06-05
Hi,
I'm making a python program and stumbled on a probably simple problem. How can you return a variable to the function that called the function that made the variable.

That probably isn't very understandable, so I'll present a small code to illustrate:

```
def one():
   variable = True
   two(variable)

   if variable == False:
      print "Yeah!"
   elif variable == True:
      print "This is what happens to me now, boooo!"

def two(variable):
   variable = False 
```

Currently, this isn't working since the variable is kept in function "two" and not exported to "one". How can I fix this?

Thanks in advance!

---

### Post by dabear on 2006-06-05
You could do it like this:
```

def one():
   variable = True
    variable = two(variable)

   if variable == False:
      print "Yeah!"
   elif variable == True:
      print "This is what happens to me now, boooo!"

def two(variable):
   variable = False
   return variable 

```
It's a workaround, 'cause I don't know how to pass variables be reference (e.g. &$variable in php) in python. You could try using globals()['variable'] though.

---

### Post by LordHunter317 on 2006-06-05
I don't see why you would in this case, want to pass-by-reference anyway.  I don't think that's a workaround, but rather the correct way.

---

### Post by Ubuntuud on 2006-06-05
I tried return, but it didn't seem to work... Does it work when the "two" is in another file, imported as a module?. Thanks!

---

### Post by 3rdalbum on 2006-06-05
Did it just return None, or did it raise a syntax error?

As long as you use the correct path for the module file, it should work. If the module name is [i]mymodule[i]:

```

import mymodule

def one():
 variable = True
 variable = mymodule.two(variable)


```

---

### Post by Ubuntuud on 2006-06-05
OK. I'll try that now. Thank you!

---

### Post by Ubuntuud on 2006-06-05
I tried with globals, which I thought was the easiest and best suiting one.

But I ran into a problem (again):

The file I run:
```
#! /usr/bin/env python

import my_module

globals()["variable"] = (raw_input("Enter: "))

my_module.function()
```

The module:
```
def function():

...do somethings with the variable...
```

But it says: "global name 'variable' in not defined"

---

### Post by DirtDawg on 2006-06-05
As I see it, there's two solutions here. First would be to contain everything in a class.
```

class thingamajig:

    def __init__(self):
        self.variable= True

    def one(self):
       self.variable = True
       self.two(variable)

       if self.variable == False:
          print "Yeah!"
       elif self.variable == True:
          print "This is what happens to me now, boooo!"

    def two(self):
       self.variable = False 

```

Conversly, just making the variable global may be your best bet. I think what you tried before was syntaxically unsound. Maybe:

```
 

variable= True
   
def one():
    global variable    ##Draws the variable from a global scope
    variable = True
    variable = two(variable)

    if variable == False:
       print "Yeah!"
    elif variable == True:
       print "This is what happens to me now, boooo!"

def two(variable):
    global variable
    variable = False
    return variable 

```

Hope this is what you're looking for.

---

### Post by DirtDawg on 2006-06-05
Looking at what I just posted, I'm not sure if you copy/pasted the code it would work, but hopefully you get the idea. :cool:

---

### Post by LordHunter317 on 2006-06-05
Again, I don't see why the variable needs to be global.  I'm not sure why you're trying to share this variable in scope, but I'm 99% positive that's the wrong thing.

An explanation of why you're trying to do this would be helpful.  DirtDawg's second example is totally wasteful, there's no need for the variable to be global.

---

### Post by Ubuntuud on 2006-06-05
I will try it global though, but I am going to sleep now,

LordHunter, I want to make a program to solve a mathematical compare (like: "2x = 4" (don't know exactly how you call it in English). To make sure that the user entered a valid form that contains a "=", doesn't contain more than one variable etc. Those functions are stored in a different file to make it easier to manage. If it doesn't seem clear to you, I could post my code (I began this morning for one hour, so it isn't very large).

---

### Post by Van_Gogh on 2006-06-05
[QUOTE=dabear]You could do it like this:
```

def one():
   variable = True
    variable = two(variable)

   if variable == False:
      print "Yeah!"
   elif variable == True:
      print "This is what happens to me now, boooo!"

def two(variable):
   variable = False
   return variable 

```
It's a workaround, 'cause I don't know how to pass variables be reference (e.g. &$variable in php) in python. You could try using globals()['variable'] though.[/QUOTE]

This to me seems the correct way to go about it, and I don't consider it a workaround either. However, I think function two should be defined before function one, as function one calls function two:

```


def two(variable):
   variable = False
   return variable 

def one():
   variable = True
    variable = two(variable)

   if variable == False:
      print "Yeah!"
   elif variable == True:
      print "This is what happens to me now, boooo!"

```
And it should work(and no, I'm too tired to check it). Just play with the "return variable" approach. It's for most uses not a a half-bad approach.

---

### Post by Ubuntuud on 2006-06-06
Yes, I could do it this way, but since I have multiple checks the code might get unneeded long. But I'll try both. Thanks!

---

