---
title: "Passing Objects To Other Objects In Python, Possible?"
date: 2009-05-27
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-05-27
Ey guys, yeah it is me again, this time with a not-so-stupid question, I hope... I am wondering if it is possible to create an object that has items in it and among them let's say there is a user name. In the initialization of that object instance, create an object that points to the newly created object, and all other objects like it with the same username.

Here is some code:
```

class User(object):
	def __init__(self,eventobj):
		self.evntObj = []
		self.evntObj.append(eventObj)
	def add (self,eventobj):
		self.evntObj.append(eventObj)
	
class event(object):
	def __init__(self,u,d,t):
		self.user = u
		self.date = d
		self.time = t

```
Is it possible to first create an event object and then get the User object to "point" to it based on the user name? Any comments appreciated. Thanks in advance.

---

### Post by Tony Flury on 2009-05-27
If i understand what you are asking the way i would do that is have the module that defines the classes also define a dictionary object, and each time you create a User object (with its own username) you add them to the dictionary (with the user name as its key.

That way you can write a "factory" method in the same module that you can pass it a User name, and it will use the dictionary to pass back the actual object.

You could (or even should) write the method so if that User name was not already in the dictionary it creates it for you, and adds it to the dictionary - so that the only thing that creates the User object is the "factory" method.

Is that what you want ?

---

### Post by StunnerAlpha on 2009-05-27
> **Tony Flury said:**
> If i understand what you are asking the way i would do that is have the module that defines the classes also define a dictionary object, and each time you create a User object (with its own username) you add them to the dictionary (with the user name as its key.

That way you can write a "factory" method in the same module that you can pass it a User name, and it will use the dictionary to pass back the actual object.

You could (or even should) write the method so if that User name was not already in the dictionary it creates it for you, and adds it to the dictionary - so that the only thing that creates the User object is the "factory" method.

Is that what you want ?
Actually, yeah I think that is exactly what I am looking for. Any tutorials or things I should know to get started? Thanks by the way.

---

### Post by delfick on 2009-05-27
this might be helpful for you 

[http://docs.python.org/reference/datamodel.html#emulating-container-types](http://docs.python.org/reference/datamodel.html#emulating-container-types)

:)


However, I'm still slightly confused as to what you're trying to ask in the first post ........

---

### Post by StunnerAlpha on 2009-05-27
> **delfick said:**
> this might be helpful for you 

[http://docs.python.org/reference/datamodel.html#emulating-container-types](http://docs.python.org/reference/datamodel.html#emulating-container-types)

:)


However, I'm still slightly confused as to what you're trying to ask in the first post ........
A little graphical representation:
```

               event obj(user C)
      -------> event obj(user A)
User A-------> event obj(user A)
      -------> event obj(user A)
               event obj(user B)
      -------> event obj(user A)
               ...

```
I figured it out any ways. I just needed to create an event object and set it to a variable, then use that variable in the declaration(constructor) of a User object as well as append the variable into the event list. The result is that both the event list and the class User point to the same address space, so modifications done by one on the data, will show up as changes if accessed by the other. I wanted it done this way to prevent making copies since the files I am using are going to potentially be very large. Thanks for the link by the way.

---

### Post by delfick on 2009-05-27
ok then.

However, I'm unsure you completely understand what's happening :)

> The result is that both the event list and the class User point to the same address space

A class is essentially a specification of an object.
An object is an instance of a class.

so when I say 
[PHP]
class thing():
    def f(self):
       print 'hello'
[/PHP]

Then this is saying that instances of this class will have a function called 'f' (that will print 'hello' to the screen when it's called).

Then to create an instance of this class (a.k.a. object) then I write 
instance = thing()

the variable 'instance' will then essentially point to that object you just created.

So when you pass it around it will still point to that object you created (unless you reassign it to something else of course :p)

..........

:)

---

### Post by xebian on 2009-05-27
Isn't everything an object in python?  So if you were able to pass on say an integer to an object then it is.

---

### Post by delfick on 2009-05-27
From what I understand, yes, essentially everything in python is an object.

including integers

even classes themselves are objects, but they're special in that they can be used to define other objects.

From what I understand of what you want, you want to define a class and then create an instance of that class for each of your files........

@anyone : feel free to correct me :p

---

