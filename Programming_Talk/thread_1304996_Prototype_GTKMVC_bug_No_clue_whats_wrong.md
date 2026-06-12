---
title: "Prototype GTKMVC bug: No clue whats wrong"
date: 2009-10-29
forum: Programming Talk
---

### Post by J V on 2009-10-29
pygtkmvc is a framework designed to help procedurals like myself to keep within the boundries of OO...

Unfortunatley, the current version doesn't support gtkbuilder, so I downloaded a prototype for the next version from sourceforge...

(Knowledge of gtkmvc recommended)

My problem is that the model object is throwing an error, which from what I can see, shoulden't exist...

```
  File "/home/j/Projects/osrs/src/controller.py", line 43, in __init__
Controller.__init__(self,model,view)
  File "/home/j/Projects/osrs/src/gtkmvc/controller.py", line 47, in __init__
    Observer.__init__(self, model, spurious)
  File "/home/j/Projects/osrs/src/gtkmvc/observer.py", line 96, in __init__
    if model: self.observe_model(model)
  File "/home/j/Projects/osrs/src/gtkmvc/observer.py", line 101, in observe_model
    return model.register_observer(self)
  File "/home/j/Projects/osrs/src/gtkmvc/model.py", line 123, in register_observer
    if observer in self.__observers: return # not already registered
AttributeError: 'MainWindow' object has no attribute '_Model__observers'
```I have no idea whats wrong with this, from what I can see there is nothing...

---

### Post by towb on 2010-04-30
You left out the important parts, namely the code you wrote, but I guess you passed view, model instead of model, view.

---

