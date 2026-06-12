---
title: "Python: Variables 'N' Classes"
date: 2010-10-12
forum: Programming Talk
---

### Post by Sailor5 on 2010-10-12
Ahoy Sailors!

So I'm giving my Twisted application an interface using PyQT, Twisted is under one class whilst PyQT is under another, When Twisted receives a certain message, I then want to display such in a QListWidget, But there's the problem, How can I share a variable between classes? eg.

```

class Alpha():
   def Foxtrot():
     print var
class Omega():
   def Whiskey():
      var = "Ahoy!"
```Obviously not the real code there but an example of the problem, Bear in mind I can't run the PyQT and pass the variable to it that way. [ [COLOR=red]PyQT(var) [/COLOR]]

Any ideas?

---

### Post by unknownPoster on 2010-10-12
Choices as I see it:
1. Your variable could be a public member of a class, making it publicly available to all classes.
2. Your variable could be a private member of your class and other classes can access it via "getter" and "setter" methods.

---

### Post by Tony Flury on 2010-10-12
You don't share variables - globals are such a bad idea.

You pass your values as arguments tot  methods that you write - and then your methods call PyQT to make your GUI do what you want.

---

### Post by nvteighen on 2010-10-13
Create an interface... but not just this time, but all times you want two "things" (object, function, whatever) communicate with each other, create a way to have them exchange data in a controlled way.

In classes, as you were told, you can either make that variables public members of your class, so that when an instance is passed you can check that variable, or make those variables private members and provide some method to get that information however you like.

Like this, using public variables (actually, Python doesn't have real private variables...):
```

class A(object):
    def __init__(self):
        self.a = 23

    def getFromB(self, myB):
        print(myB.b) # Accessing the b value of a B instance.

class B(object):
    def __init__(self):
        self.b = 1

    def getFromA(self, myA):
        print(myA.a) # Accessing the b value of a B instance.

```

---

