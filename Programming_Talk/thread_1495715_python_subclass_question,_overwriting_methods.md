---
title: "python subclass question, overwriting methods"
date: 2010-05-28
forum: Programming Talk
---

### Post by mo.reina on 2010-05-28
overwriting class methods, from the wxpython wiki:

```
class MyFrame(wx.Frame):
    def __init__(self, parent, title):
        wx.Frame.__init__(self, parent, title=title, size=(200,100))
```

my question is, why can't we simply do (forgoing the size setting for the moment):

```
class MyFrame(wx.Frame):
    def __init__(self, parent, title):
```

the above example won't work, but i'm curious to know why and what is going on in the first example that makes it work...

---

### Post by smartbei on 2010-05-28
The wx.Frame class's __init__ method has important code of its own, and in python, the constructor of a parent class isn't called automatically.

In this case specifically, the Frame must register itself with wx so that it can be displayed.

Did that answer your question?

---

### Post by StephenF on 2010-05-28
> **smartbei said:**
> In python, the constructor of a parent class isn't called automatically.
Just to clarify:

The __init__ of the class is always called but if you provide your own __init__ in a subclass it is up to you, the programmer, to provide code to call the __init__ in the parent class.

Where no __init__ is provided in the subclass the __init__ method of the parent class is inherited and will be called as the constructor method. This is preferable to creating an __init__ whose sole purpose is to call __init__ of the parent class.

---

### Post by mo.reina on 2010-05-28
> **StephenF said:**
> Just to clarify:

The __init__ of the class is always called but if you provide your own __init__ in a subclass it is up to you, the programmer, to provide code to call the __init__ in the parent class.


but if you provide your own __init__, why do you still have to call the __init__ of the parent class?  providing your own __init__ should overwrite the __init__ of the parent class, yet this isn't the case, you must also call the __init__ of the parent class...

---

### Post by trent.josephsen on 2010-05-28
> **mo.reina said:**
> but if you provide your own __init__, why do you still have to call the __init__ of the parent class?  providing your own __init__ should overwrite the __init__ of the parent class, yet this isn't the case, you must also call the __init__ of the parent class...

The child constructor *does* overwrite the parent constructor, and that is *exactly why* you have to call the parent constructor manually.  When you write an __init__ method, or any method, inside a class, and then call the method through the class, Python will stop searching the inheritance tree immediately because the method is a member of the class.  Python won't call things for you behind the scenes.  "Explicit is better than implicit."

Would you expect parent constructors to be called automatically?  Well, what if you inherit from more than one class -- should they all be called?  In what order?  With what arguments?  What if there are two or more conflicting constructors in the parent class?  Consider the following class structure:

```
class Shape:
    def __init__(self, sides=None):
        self.sides = sides
    def __str__(self):
        if self.sides == None:
            return 'I am a generic Shape.'
        else:
            return 'I have ' + str(self.sides) + ' sides.'

class Triangle(Shape):
    def __init__(self):
        Shape.__init__(self, 3)

class Quadrilateral(Shape):
    def __init__(self):
        Shape.__init__(self, 4)
```

In this case, it's necessary to call the parent constructor explicitly because otherwise it wouldn't be possible to specify the number of sides as is necessary.  Other cases come to mind where processing needs to be done and decisions need to be made about **what to pass** to the parent constructor.  Python isn't psychic.

---

### Post by mo.reina on 2010-05-30
ok i understand now, thanks

---

