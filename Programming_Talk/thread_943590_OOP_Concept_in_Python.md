---
title: "OOP Concept in Python"
date: 2008-10-10
forum: Programming Talk
---

### Post by ApostleofJesus on 2008-10-10
Hello All,
Greetings!
I have question concerning OOP with Python. Any other opinion a part from py is allowed but I know that Language. I want to know when Python class or being specific, how py class ends in package like wxpython.

What I mean is I have one class let say of frame and another class of a dialog box all in same py file. When Frame runs, uses self i.e self.button = wx.Button. This object belongs to frame. And let say we have text control in the other class (dialog). How do I call method of another class from the other class, i.e how do I call button from dialog and dialog from button.

Suppose I want to manipulate the button, let say its label, but from another class which it doesn't belong (In this case Dialog)?

Lastly: What is relation between classes, objects, modules? I have tried to learn myself, but I find hard to grasp the real concept!

Thank you guys and girls for your help
Steve:)

---

### Post by LaRoza on 2008-10-10
> **ApostleofJesus said:**
> 
Lastly: What is relation between classes, objects, modules? I have tried to learn myself, but I find hard to grasp the real concept!


A class is:

```

class ClassExample:
    def __init__(self):
        print "I am a class"

```

An object is:

```

x = ClassExample()
#x is an object

```

A module is just a collection of code (usually, classes and functions) that can be used.

So:

```

import os 
#os is a module

```

---

