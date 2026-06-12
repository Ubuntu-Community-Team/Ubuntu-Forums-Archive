---
title: "A question about objects in Python"
date: 2008-03-30
forum: Programming Talk
---

### Post by xelapond on 2008-03-30
Hello, 

I have never programmed with Object Oriented stuff before, so I am really struggling to get it to work.  I understand the concept, that you can have multiple instances of an object, and that these instances can have methods, but I my main problem lies with instances and what to do with them.  Consider the following code:

```
def connect_server(pass some stuff):
     Do some stuff
     instance1 = module1.class1(some stuff)
```

This creates an instance of class1, instance1.  Now, what do I do with instance1 if I want other functions to be able to access and do it?  Do I return it?  Like this?

```
def connect_server(pass some stuff):
     Do some stuff
     instance1 = module1.class1(some stuff)
     return instance1

instance1 = connect_server(pass some stuff)

instance1.method1(pass some stuff)
```

And make is global?  Or do I pass it into each function?  Or am I totally missing the point?  For a final question, how do I make other modules access that instance?

Thanks, 

Alex

---

### Post by Wybiral on 2008-03-30
Everything in Python is an object:

```

isinstance(1, object)
isinstance("", object)
isinstance([], object)
isinstance({}, object)
isinstance(cmp, object)

```

Just treat objects like any other variable. If you've ever assigned the value "1" to a variable, you've used an object.

---

### Post by xelapond on 2008-03-30
OK, that helps, but I am still a little bit foggy on how to access them between modules.  If Module1 creates instance1, how does Module2 get access to it?'

Thanks, 

Alex

---

### Post by pmasiar on 2008-03-30
Every variable you used in Python so far is instance of some kind of class. Don't force objects on yourself, start programming, and when you will have something with multiple properties and methods, you call it object. It is simple to program in Python old-fashioned "procedural" way, without defining your own objects (just use the ones provided by libraries), until you are ready for OOP.

---

### Post by pmasiar on 2008-03-30
> **xelapond said:**
> If Module1 creates instance1, how does Module2 get access to it?'


You need to pass the instance. Every variable is object, there is no difference between objects of classes provided by system, and your own custom classes. It is just variable, name referring to instance of something.

---

