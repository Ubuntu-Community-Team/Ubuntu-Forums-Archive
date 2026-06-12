---
title: "Python Class Question"
date: 2009-05-21
forum: Programming Talk
---

### Post by prem1er on 2009-05-21
I am new to python and this is the first time I have been using different classes in a script.  I am trying to implement the pyinotify module to help me monitor a directory. From the [website]("http://trac.dbzteam.org/pyinotify/wiki/Tutorial").

```
from pyinotify import WatchManager, Notifier, ThreadedNotifier, ProcessEvent, IN_DELETE, IN_CREATE

wm = WatchManager()

mask = IN_CREATE

class PTmp(ProcessEvent):
    def process_IN_CREATE(self, event):
        print "Creating:", event.pathname
```


But instead of printing the 'event.pathname', I want to return that variable to another class. 

```

p = PTmp()
notifier = Notifier(wm, p)
wdd = wm.add_watch('/tmp', mask, rec=True)
notifier.loop()

```

How can this be accomplished? Or could you link me to a good reference about returning values from classes.  Thank you.

---

### Post by sloggerkhan on 2009-05-21
typically a method has a return value while an instance of a class will have getter/setter methods.

---

### Post by prem1er on 2009-05-21
> **sloggerkhan said:**
> typically a method has a return value while an instance of a class will have getter/setter methods.

Yes, so I'm assuming I need something like this.

```
class PTmp(ProcessEvent):
    def process_IN_CREATE(self, event):
       return event.pathname
```

But how do I use that value?

---

### Post by unutbu on 2009-05-21
prem1er, why not build the functionality into the PTmp class? It would be the natural class to handle the IN_CREATE event. 

However, if you really want to send the event to another object, you would need to make PTmp aware of what object to use. You could do that be initializing PTmp with an argument like this:
[PHP]
    def __init__(self,an_obj):
        self.an_obj=an_obj[/PHP]

Then you could call any method known by an_obj. For example,
[PHP]
    def process_IN_CREATE(self, event):
        self.an_obj.record(self.path(event))[/PHP]

Here is some simple code, implementing the above:

[PHP]#!/usr/bin/env python
import sys
import os
from pyinotify import WatchManager, Notifier, EventsCodes, ProcessEvent

class AnObject(object):
    def record(self,astr):
        print('AnObject.record() called: %s'%astr)

class PTmp(ProcessEvent):
    def __init__(self,an_obj):
        self.an_obj=an_obj
    def process_IN_CREATE(self, event):
        self.an_obj.record(self.path(event))
    def path(self,event):
        return event.name and os.path.join(event.path, event.name) or event.path

if __name__=='__main__':
    an_obj=AnObject()
    wm = WatchManager()
    mask = EventsCodes.IN_CREATE
    notifier = Notifier(wm, PTmp(an_obj))
    wdd = wm.add_watch('/tmp', mask, rec=True)
    while True:  
        try:
            notifier.process_events()
            if notifier.check_events():
                notifier.read_events()
        except KeyboardInterrupt:
            notifier.stop()
            break
[/PHP]

---

### Post by prem1er on 2009-05-21
Thank you for your post. After some reading I found I should be doing exactly as you have mentioned here...

> prem1er, why not build the functionality into the PTmp class? It would be the natural class to handle the IN_CREATE event. 

Problem is I still can't work out how to get the event.pathname to be returned, even in the same class.

---

### Post by unutbu on 2009-05-21
Well, first off, I don't think the event object has an attribute called pathname.
It has event.name and event.path attributes however, and the method

```
    def path(self,event):
        return event.name and os.path.join(event.path, event.name) or event.path

```
can be used to provide you with a full path name.

Next, don't think about giving process_IN_CREATE a return value -- nothing will be listening for it on the other end. Instead, just call another function. For example,
```

    def my_method(self,event):
        ...
    def process_IN_CREATE(self, event):
        self.my_method(event)
```

But then again, don't forget that it is also possible to just put the code in 
process_IN_CREATE.

---

### Post by prem1er on 2009-05-21
> Well, first off, I don't think the event object has an attribute called pathname.
It has event.name and event.path attributes however, and the method


I think it does, but am not sure.  When I was just doing...

```
print event.pathname
```

I was getting the name of the file created, so that seems to be fine.  But thank you for your responses I will look it over in more detail when I get back home.  Thanks again!

Edit:  I think I see exactly what you meant in your last post.

---

### Post by unutbu on 2009-05-21
> **prem1er said:**
> I think it does, but am not sure.  When I was just doing...

```
print event.pathname
```

I was getting the name of the file created, so that seems to be fine.

Ahh. The pyinotify that ships with Jaunty has an Event class with a pathname attribute. ([http://trac.dbzteam.org/pyinotify/wiki/DocumentationPage](http://trac.dbzteam.org/pyinotify/wiki/DocumentationPage))
Intrepid's pyinotify lacks this attribute. ([http://pyinotify.sourceforge.net/#The_Event_Class](http://pyinotify.sourceforge.net/#The_Event_Class))

---

