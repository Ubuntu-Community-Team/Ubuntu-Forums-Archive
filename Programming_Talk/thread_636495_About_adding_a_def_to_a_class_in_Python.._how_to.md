---
title: "About adding a def to a class in Python.. how to?"
date: 2007-12-09
forum: Programming Talk
---

### Post by thenetduck on 2007-12-09
Hi

I am making a program (my first OOP in python) and I noticed that you have to call the functions that you def after you create them ie: calling the def at the bottom of the page. I was wondering, is there something like in C++ where you can tell the class what def or functions can be used at the top of the page so I can call them from anywhere in the page? Thanks

The Net Duck

---

### Post by cwaldbieser on 2007-12-09
> **thenetduck said:**
> Hi

I am making a program (my first OOP in python) and I noticed that you have to call the functions that you def after you create them ie: calling the def at the bottom of the page. I was wondering, is there something like in C++ where you can tell the class what def or functions can be used at the top of the page so I can call them from anywhere in the page? Thanks

The Net Duck

In Python, the def statement creates a function object-- it is not a declaration.  So you need to create a function before you can call it.  As long as the function actually exists at the point you try to call it, there will not be an error.

---

### Post by thenetduck on 2007-12-09
So what you are saying is... no you can't pre write the functions at the top like in C++. Err.. anyway, ok I can deal with declaring stuff below it. But what if I need to jump around? Inconvienent!

---

### Post by xtacocorex on 2007-12-09
> **thenetduck said:**
> So what you are saying is... no you can't pre write the functions at the top like in C++. 
Just define all your functions before you call:
```
if __name__ == "__main__":
```
and you shouldn't have ay problems

---

### Post by tyoc on 2007-12-09
That is not a "problem"

```

class Nada:
    def k1(self):
        nada2 = Nada2()
        nada2.k1()
        print "k1"
        self.k2()

    def k2(self):
        print "k2"
        

class Nada2:
    def k1(self):
        print "Nada2:k1"

x = Nada()
x.k1()

```I guess that is enough, also you can put a name like file.py and them import it in another file.

Or that is not what are you trying to accomplish?
------------------------

On the other hand, the declaration of classes or functions in the header files, is exactly put a forward reference to the functions, because they cant adivine what names and args you will use for functions, but in this case, there is no "declaration" and "implementation" separated from each other (just like java IIRC), then yes, you should declare/implement them before **use them** see that instead I was able to put a forward reference in **Nada1** to **Nada2**, but that actually is not something that will be executed "now", it will be read and the forward reference solved when it find it (when it get the Nada2 class), and used finally when actually instantiating an object with x = Nada() the definition/implementations will be used.

---

