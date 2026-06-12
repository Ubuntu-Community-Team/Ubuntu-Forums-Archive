---
title: "beginner who needs some help"
date: 2014-06-26
forum: Programming Talk
---

### Post by lucas21 on 2014-06-26
hey my name is lucas and i just started coding apps for ubuntu. now i have a few problems, mostly with finding the informations that i need.
so i have like two main questions.

fist, were can i find all the funkts and vars that a object like a text entry or a button has? an how to change it in python scrips? ( im using the quickly building apps thingy. also for editing ui im using glade and for python sublime text )
also i would like to know if sublime text and glade is the best way to go in ubunut development.

than you so much for for the help this forum and the community is just so much better and nicer than every microsoft forum i have ever been on.

---

### Post by donkyhotay on 2014-06-27
There is no one answer because the functions and variables that an object can have depend on the object. Thats the entire point of an object. You could create an object "fruit" and theoretically give it variables of "taste", "color" and the function "rot". On the other hand the object "knife" would have variables "color", "sharpness" and function "cut". Now if you code the object yourself then you should know what it does, but if you're using an object from a library someone else made then you need to look at it's documentation. From your post I think you're using python. For information on the standard modules that come with python I would start here: [https://www.python.org/doc/](https://www.python.org/doc/), but if for example you import a new library like say pygame for example, then you would need to look at the pygame site for documentation on what it has.

---

### Post by ofnuts on 2014-06-27
In Python you can use dir(object) to find all the attributes/methods it supports. If the info is provided (as part of the source code) then  you can use help(method) to get documentation about it. But a paper doc or a site may explain things not in this kind of documentation.

About changing objects: normally you don't change the code, you implement a derived class, in which you define the methods added/changed from the base class. In other words, a "Dog" is a "Mammal" to which you add a "bark()" method (prints "Woof!"). Then you create instances of "Dog" to fill your kennel. You can also create a "Poodle" class that derives "Dog" in which bark() prints "Ouaf!" (because poodles bark in French).

```

class Dog(object):
    def bark(self):
        print 'Woof!'

    def waggleTail(self):
        print '*waggling tail*'

class Poodle(Dog):
    def bark(self):
        print 'Ouaf!'


dog1=Dog()
dog1.bark()
dog1.waggleTail()
print '-----------'
dog2=Poodle()
dog2.bark() # in French
dog2.waggleTail() # still valid because it's also a Dog

```

Typically when you design a GUI you derive the standard widgets classes to implement your required behavior.

---

### Post by lucas21 on 2014-06-27
thanks i never thought of reading the official documentation... im so stupid sometimes :/
but what about the editors?

---

### Post by donkyhotay on 2014-06-28
What about editors? Editors are tools that can help with their own advantages and disadvantages. You ask 5 different programmers the best editor to code in and a you'll get 6 different answers. Personally I prefer to do all my coding in gedit. It's light, has all the features I need, and pretty easy to figure out. The ones I hear about the most for linux gedit, eclipse, vi and Emacs. I found eclipse to be too bloated for my taste while vi and emacs are a bit too arcane. I do have to say though that while the people that vouch for vi and emacs sometimes seem elitish, if you can master those two you can practically fly through them. For times when I'm without a GUI I use nano. It doesn't have everything I want (though it has more then is readily apparent) but everything else I've found for CLI is either to slow or well... vi or Emacs. Of course what works for me won't necessarily work for you. Play around with different tools and eventually you'll find what works best for you.

---

### Post by lucas21 on 2014-06-28
thanks a lot! :)

---

