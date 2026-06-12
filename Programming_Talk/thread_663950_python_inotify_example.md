---
title: "python inotify example"
date: 2008-01-10
forum: Programming Talk
---

### Post by alef13 on 2008-01-10
Simple code to monitor CLOSE events on specific directory using Python pynotify.

```

#!/usr/bin/env python

import os, sys
from pyinotify import WatchManager, Notifier, ProcessEvent, EventsCodes

def Monitor(path):
    class PClose(ProcessEvent):
        def process_IN_CLOSE(self, event):
            f = event.name and os.path.join(event.path, event.name) or event.path
            print 'close event: ' + f

    wm = WatchManager()
    notifier = Notifier(wm, PClose())
    wm.add_watch(path, EventsCodes.IN_CLOSE_WRITE|EventsCodes.IN_CLOSE_NOWRITE)

    try:
        while 1:
            notifier.process_events()
            if notifier.check_events():
                notifier.read_events()
    except KeyboardInterrupt:
        notifier.stop()
        return


if __name__ == '__main__':
    try:
        path = sys.argv[1]
    except IndexError:
        print 'use: %s dir' % sys.argv[0]
    else:
        Monitor(path)

```

---

### Post by skeswani on 2008-01-15
I happened to write a similar application to monitor any arbitrary event and run a system command when it happens, albeit, this is in C.

[http://www.qautils.org/mediawiki/index.php/Watchfs](http://www.qautils.org/mediawiki/index.php/Watchfs)

Was usefull when testing applications

---

### Post by sanraj83 on 2008-08-04
Hi Alef;

When I try to run this code I get the following error. Do you know why ?

<type 'exceptions.AttributeError'>: type object 'EventsCodes' has no attribute 'IN_CLOSE_WRITE'


Can you give me your thoughts / tell me where I am erring ? 

Thanks

RxS

---

### Post by catchmeifyoutry on 2008-08-04
> **sanraj83 said:**
> Hi Alef;

When I try to run this code I get the following error. Do you know why ?

<type 'exceptions.AttributeError'>: type object 'EventsCodes' has no attribute 'IN_CLOSE_WRITE'


Can you give me your thoughts / tell me where I am erring ? 

Thanks

RxS

Hm, his/her code works for me, what version of pyinotify are you using?
I got 0.7.1-1 from the Hardy repository.
Otherwise, try these python commands
[PHP]
import pyinotify
print dir(pyinotify.EventsCodes)
[/PHP]
and see if IN_CLOSE_WRITE shows up.

---

### Post by pic123 on 2008-08-11
same happend to me - until i realised that there is a major syntax change in version 0.8.xxx. Read the NEWS file - helps always a lot.

---

### Post by yahmad on 2009-03-05
HI,

I was wondering if someone could help me with an issue I am having with the pyinotify lib that is built on inotiify.

I am currently trying to monitor some files and directories on a samba server that is mounted on my linux server. However, any changes made by others on the samba server are not picked up by my script. If I make changes to files on the server while I am logged in to my linux server, then I see events raised. 

Do any special configuration details have to be set? 

Thanks.

---

### Post by dwiel on 2009-11-14
The news that pic123 is referring to is:

```
EventsCodes.IN_* replaced by IN_* (avalaible at the pyinotify's scope)
```

---

### Post by jav on 2010-08-23
So, in regard to the mentioned changes in 8.
How should I change my software?

Today I'm using 
```
exec("mask |= EventsCodes." + evcode)
```

I'm guessing it should be something like
```
exec("mask |= " + evcode)
```
But with some namespace ... something...

---

### Post by juancarlospaco on 2010-08-23
1 import per line :)

---

### Post by 6ixth on 2010-11-11
The docs, tutorials and websites are outdated.
The only thing up to date i found are the examples here:
[https://gith*******/seb-m/pyinotify/tree/master/python2/examples](https://gith*******/seb-m/pyinotify/tree/master/python2/examples)

If you are getting errors like


<type 'exceptions.AttributeError'>: type object 'EventsCodes' has no attribute 'IN_*'

Then you have to do something like

```
import pyinotify
mask = pyinotify.IN_MODIFY # watched events

```

---

### Post by alfalfa55 on 2012-03-27
> **catchmeifyoutry said:**
> Hm, his/her code works for me, what version of pyinotify are you using?
I got 0.7.1-1 from the Hardy repository.
Otherwise, try these python commands
```

import pyinotify
print dir(pyinotify.EventsCodes)

```and see if IN_CLOSE_WRITE shows up.

I get:
```

Python 2.6.6 (r266:84292, Nov 28 2011, 23:30:22) 
[GCC 4.5.3] on linux3
Type "help", "copyright", "credits" or "license" for more information.
>>> import pyinotify
>>> print dir(pyinotify.EventsCodes)  
['ALL_FLAGS', 'ALL_VALUES', 'EVENT_FLAGS', 'FLAG_COLLECTIONS', 'OP_FLAGS', 'SPECIAL_FLAGS', '__class__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__hash__', '__init__', '__module__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'maskname']
>>> 
```

---

