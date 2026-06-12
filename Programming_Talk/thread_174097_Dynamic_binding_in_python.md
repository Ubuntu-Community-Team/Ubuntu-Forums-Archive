---
title: "Dynamic binding in python"
date: 2006-05-11
forum: Programming Talk
---

### Post by [h2o] on 2006-05-11
I am new to python and ran into something which I found really strange: dynamic binding does not seem to work at all?

If I have the following to classes (with unneccessary functions removed):

```
class Person:
  """Defines a general person """
  
  def __description(self):
	return "Person function"

  def printInfo(self):
    print self.__description()

class Parent(Person):
"""Defines a parent """
  def __description(self):
    return "Parent function"

```


But when I run
 ```

a = Person()
b = Parent()
a.printInfo()
b.printInfo()

```
both calls return "Person function" instead of "Person function" and "Parent function"

In java, which I am more familiar with, the rte checks what type of object the instance is and then executes the correct function (Parent.__description for a Parent-object and Person.__description for a Person object) but python seems to not do this. Actually, if I change my "printInfo" function to "print  self.__description" it clearly shows that Person-objects return "<bound method Person.__description of ..." while Parent-objects return "<bound method Parent.__description of ..." so I really can't understand why it won't work!

What am I missing?

---

### Post by yaaarrrgg on 2006-05-11
Hmmm... I noticed that if you add:

```

  def printInfo(self):
    print self.__description()

```

to the subclass, it works. This does not seem intuitive to me either.  I'd guess it's casting self to Person and then it can't find the "Parent" method?

---

### Post by ow50 on 2006-05-11
Use single underscore, if there's inheritance. Double underscore names are mangled.

There's something about single vs. double underscores in [PEP 8](http://www.python.org/dev/peps/pep-0008/), perhaps more of the technical aspects elsewhere.

---

### Post by [h2o] on 2006-05-11
Hmm, but isn't double underscores what makes a function private?
If so, then how do you make a private function work with dynamic binding?

---

### Post by LordHunter317 on 2006-05-11
[QUOTE='[h2o]']If so, then how do you make a private function work with dynamic binding?[/QUOTE]You cannot.  That's contradictory with the definition of 'private'.  You can't provide a new implementation to something you don't have access to.

---

### Post by ow50 on 2006-05-11
Single underscore names are used for private attributes. It just requires responsible use since there no actual mechanism preventing access to them. Double underscore names are more private, used when you don't want them inherited. There's class specific name mangling to prevent accidental access, but variables are still accessible using the mangled forms of the names. Neither one is private to bad-habited programmer.

So, you'll want to use
```
def _description(self):
    return ...
```

---

### Post by [h2o] on 2006-05-11
[QUOTE=LordHunter317]You cannot.  That's contradictory with the definition of 'private'.  You can't provide a new implementation to something you don't have access to.[/QUOTE]
True... I was looking for a python equivalent of "protected". My bad.

Replacing __description with _description solved my problem. Thank you ow50 :)

---

