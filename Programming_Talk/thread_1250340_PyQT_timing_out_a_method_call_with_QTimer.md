---
title: "PyQT: timing out a method call with QTimer?"
date: 2009-08-26
forum: Programming Talk
---

### Post by lykwydchykyn on 2009-08-26
Here's the scenario:  I have a KDE applet that I'm working on which uses a python library (dictclient) that makes network calls but does not have any kind of timeout implemented.

I need to implement a timeout for this operation in my program, otherwise it does really bad things when it just never returns from the call.

I thought I could do something like this, but it isn't working:

```

try:
    timer = QTimer(self)
    self.connect(timer, SIGNAL("timeout()"), self.method_that_raises_exception)
    timer.start(2000)
    self.method_foo()#the one that needs a timeout
    timer.stop()
except:
    print "timeout error"

```            

The problem is, it never raises the exception if the method foo locks it up.  Do I need to make method_foo run in a separate thread?

Or am I missing a quick and simple way to timeout a python function call?

---

