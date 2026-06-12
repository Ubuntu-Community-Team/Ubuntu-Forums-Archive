---
title: "[Python] Instances to declare it's maker (variable)"
date: 2010-06-01
forum: Programming Talk
---

### Post by Kegusa on 2010-06-01
Kind of a tricky one. 

I have loads of generator classes producing GUI components and in so doing I would like to identify the maker of an instance.

```
class A():

	def __init__(self, name):
		""" Generator stuff """

	def output(self):
		""" Generated results """

a = A(name).output()

# Then do something more with a 

```

It's easy enough to identify the generated classes and subclasses with __class__ and __bases__ , but to have an identifier that can  make the instance tell me what variable that initiated the class call is another matter for me..

Anyone with thoughts on this? a sort of operator overloading or am I too deep in it to see the easy solution? :)

---

### Post by Can+~ on 2010-06-01
I think it's possible, but my first question is... why?

For instance, say that you do:

[PHP]a = myclass()
b = a
a = "Hello World"
# b now holds the class, a is something else[/PHP]

a is no longer relevant to the class, yet you would hold it as the "creator".

I feel that you're breaking some fundamental rule, I couldn't tell you which one, but I smell something wrong.

---

### Post by Kegusa on 2010-06-02
After a couple of more cups of coffee and a break I figured an easier way and keeping to the rule of KISS (Keep it simple stupid).

The whole problem was classes generating mutated instances spawning new subclasses generating more etc.etc. (and coupling with older "genes".)

Just added a tracker instead and let the spawns tell the tracker what happens, instead of asking each and every spawns offspring what and where it comes from. 

Still curious if it's possible and how it can be done, but will have to figure that out later. Even if it breaks with conventions and ties the PEP8 into a knot and tosses it into a fire, knowledge is knowledge :)

---

### Post by nvteighen on 2010-06-02
I still don't get what you want... I mean, why the hell would you like to keep track of the origin place of allocation for an object when you already have a way to get access to that same object?

Your "genetic" idea is actually something absolutely different... you're simulating "origin" and have devised a way to keep track of it... referencing objects not "places" (take "place" as defined by Common Lisp...). Such a tracker has nothing to do with the allocation, but with the "world" you're constructing.

Were C double pointers your inspiration? I ask you that because in theory, C double pointers could serve you for this, but only because of an optical illusion... what you could do with them is just to hold a memory address of where that object was created, but you'd have no way to check whether that address is still valid or not without risk of crashing your program.

---

