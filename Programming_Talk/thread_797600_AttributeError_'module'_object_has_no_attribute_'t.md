---
title: "AttributeError: 'module' object has no attribute 'test'"
date: 2008-05-17
forum: Programming Talk
---

### Post by hannulan on 2008-05-17
What does this message mean?

I have a class called diagram and one called kalender with the constructors __init__(self,frame) and __init__(self,frame,diagram)

In the constructor in the kalender class (created after the diagram) I then want to call the function test(self,text) wich is an attribute to the diagram class.

I have done that in different ways, but not with any success.

__init__(self,frame,diagram)
self.Diagrammet = diagram
self.Diagrammet.test()
give me the error "AttributeError: 'module' object has no attribute 'test'"

which also is the result from the code:
diagram.test()

Can someone explain what I'm doing?

---

### Post by dwhitney67 on 2008-05-17
Dunno, without seeing all of your code.  I don't know Python, yet was able to code this example in a few minutes.  It works!

[PHP]#!/usr/bin/python

class Diagram:
        def __init__(self, text):
                self.text = text
        def test(self):
                print self.text

class Kalendar:
        def __init__(self, diagram):
                self.diagram = diagram
                self.diagram.test()


d = Diagram( "Hello World" )
k = Kalendar( d )
k2 = Kalendar( Diagram("Again, Hello World") )[/PHP]

---

### Post by WW on 2008-05-17
My guess is that the **diagram** class is defined in one file, and **import**ed in the file that causes the error.  You appear to be passing the module name to the kalendar constructor, instead of passing an instance of a diagram object.  We need to see more of the code to be sure.

For example:

**diagram.py**
```

class diagram:

    def __init__(self, text):
        self.text = text

    def test(self):
        print self.text

```

**atest.py**
```

import diagram

class kalendar:
    def __init__(self,diagram):
        # Warning: "diagram" is a bad choice of a variable name here!
        self.diag = diagram
        self.diag.test()

# This works...        
k1 = kalendar(diagram.diagram("Hello, world!"))

# This causes the error message...
k2 = kalendar(diagram)

```

Run:
```

$ python atest.py 
Hello, world!
Traceback (most recent call last):
  File "atest.py", line 12, in <module>
    k2 = kalendar(diagram)
  File "atest.py", line 7, in __init__
    self.diag.test()
AttributeError: 'module' object has no attribute 'test'
$ 

```

---

### Post by sznurek on 2008-05-18
> **WW said:**
> 
```

k2 = kalendar(diagram)

```

You are passing module to kalendar constructor - it should be diagram.diagram("xxx").

**diagram** is a module. It contains class **diagram**. This class contains method **test**.

---

