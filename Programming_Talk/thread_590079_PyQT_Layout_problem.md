---
title: "PyQT Layout problem"
date: 2007-10-24
forum: Programming Talk
---

### Post by happysmileman on 2007-10-24
I'm in PyQt and trying to add a Widget into a QGridLayout at a specified position taking up more than one row or column, but can't do it.

I'm trying to use this code:

```
self.counter = QLCDNumber(2, self)
self.layout.addWidget(self.counter, 0, 0, 0, 2)
```

Which should work in C++ because it overrides the AddWidget function, however in Python, since there's no function overloading, it won't work and says I need a maximum of 4 arguments. The error is

> File "./Main.py", line 25, in addWidgets
    self.layout.addWidget(self.counter, 0, 0, 0, 2)
TypeError: too many arguments to QGridLayout.addWidget(), 4 at most expected

I'm aware I could create layouts within layouts but don't want to bother for such a simple program, so any idea how to add widgets to layouts at a specified location with variable width?

---

### Post by happysmileman on 2007-10-25
Anyone? I assume someone here must've encountered this before.

---

