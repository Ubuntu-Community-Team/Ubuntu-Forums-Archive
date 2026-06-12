---
title: "Python help"
date: 2007-11-08
forum: Programming Talk
---

### Post by louis_nichols on 2007-11-08
Hi!

I need some help with 2 issues about python. I am not a complete newb but, although it seems to me that these are not difficult questions, I can not find the answer.

[LIST=1]
[*]I am trying to make a list and leave it empty but force the data type it should contain, but I don't know how.
[*]I am trying to place some data in a easily accessible manner, something like: element.propertyGroup1.property1 = value, but do it programmatically (i.e. I don't know the exact names of propertyGroup and property when I write the program). This is similar to how pyparsing can arrange data when using Dict.
[/LIST]

Any help will be greatly appreciated. Thank you!

---

### Post by smartbei on 2007-11-08
Both of these are somewhat unpythonic in nature. The first goes against the idea of dynamic casting. The second is a perfect dictionary application.
Still:

For the first you could make a class that extends the list class and override its .append method to check for a certain type, probably given to the constructor. You may also need to override some other methods in order to make sure the user doesn't change the objects type in another way.

For the second you might be able to catch the error that comes with trying to access a non-existent member variable and use it to create the variable and initialize it to the input value - no warranty on that (might not be practical/possible).

---

### Post by aquavitae on 2007-11-08
Not sure about the first - but I've found whenever I want to do something like that its because there's a problem in my design.  I'm basically a c++ programmer so I tend to think in types.  In python, you shouldn't.

The second - have a look at the __getattr__, __setattr__ and __delattr__ special class methods.  I haven't used them but it looks like what you want.

---

### Post by louis_nichols on 2007-11-08
Thank you very much for the replies! I understand better now. I think I will drop both ideas. :)

For the first issue, I will just be careful at the items I place in the list (I am the only programmer of the application). The thing was that I have a class I made and I wanted to make another class which contains an attribute that is a list of instances of the first class (complicated?). But I'll just be careful to place only that kind of objects in the list...

For the second, I'll just use a dictionary. I got the idea from pyparsing and I htink it offers a more simple syntax, but a dict will do.

Again, thank you very much for your answers! Take care!

---

### Post by pmasiar on 2007-11-08
> **louis_nichols said:**
> 

1) I am trying to make a list and leave it empty but force the data type it should contain, but I don't know how.

When you use [http://en.wikipedia.org/wiki/Duck_typing](http://en.wikipedia.org/wiki/Duck_typing) , you don't care about the exact type. If you want to code defensively, you either check if type has methods you need, or  catch the exception.

> 2) I am trying to place some data in a easily accessible manner, something like: element.propertyGroup1.property1 = value, 

If you use dictionary, key can be a tuple: element[group, property] = value.

---

