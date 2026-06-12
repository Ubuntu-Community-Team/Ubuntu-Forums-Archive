---
title: "Python: class called from another class can't access attribute"
date: 2011-06-17
forum: Programming Talk
---

### Post by Uchiya on 2011-06-17
Sorry if the title is not correct, I don't know how to explain better.

I want the class EventHandler to be able to use/see the variable "file". How can I do that? 
```

class app:
    def __init__:
    self.file=open("file.txt")
    n=pyinotifier.threadedNotifier(blah, EventHandler())
    
    def choosefiledialog(self):
         #code to choose file

class EventHandler(pyinotify.ProcessEvent)
   def IN_MODIFY(self,event)
       #Stuff to do when event is received
      file.something()

if __name__ = "main":
a=app()

```

---

### Post by nzjethro on 2011-06-17
Hi there, I'm quite new to Python, but I believe you could declare the file object as global, using

```
class spam:
        global file
        def eggs():
            rest of code here
```

While this will work, I think most Python purist frown upon globals, and prefer to use set() and get() methods (my background is Java, so I may be calling them the wrong thing here).

---

### Post by simeon87 on 2011-06-17
In some frameworks you can pass additional arguments to an event handler. In that case it would look like:

```
class app:
    def __init__:
    self.file=open("file.txt")
    n=pyinotifier.threadedNotifier(blah, EventHandler(), self.file)
    
    def choosefiledialog(self):
         #code to choose file

class EventHandler(pyinotify.ProcessEvent)
   def IN_MODIFY(self,event, f)
       #Stuff to do when event is received
      f.something()

if __name__ = "main":
a=app()
```

But if your framework doesn't support that then that's not possible. In that case you could pass the file to the event handler upon construction:

```
class app:
    def __init__:
    self.file=open("file.txt")
    n=pyinotifier.threadedNotifier(blah, EventHandler(self.file))
    
    def choosefiledialog(self):
         #code to choose file

class EventHandler(pyinotify.ProcessEvent)
   def __init__(self, f):
       self.file = f
   def IN_MODIFY(self,event)
       #Stuff to do when event is received
      self.file.something()

if __name__ = "main":
a=app()
```

Not necessarily the prettiest solution but it works. Otherwise you end up working with globals.

---

### Post by Tony Flury on 2011-06-17
You need to make sure your Event Handler Class knows about the instance of the app class - i would suggest passing the app class as a parameter as suggested by simeon87

I would not suggest the global route. You could have a singleton pattern - and do it properly via a singleton class and an access method, but i would go the parameter route.

I actually think that the global directive is something that Python has got very wrong - it encourages poor design and it is always possible to design code without globals.

---

