---
title: "Timer module, to be opened from within another python program"
date: 2007-08-31
forum: Programming Talk
---

### Post by DamjanDimitrioski on 2007-08-31
Hi! :)
The program is separated in two modules:
Module I>
```

#! /usr/bin/env python
# -*- coding: utf-8 -*
# -*- Mode: Python -*-
import sys
import time
import threading
class Timer(threading.Thread):            
   def __init__(self, seconds):        
      self.runTime = seconds
      threading.Thread.__init__(self)
   def run(self):
      time.sleep(self.runTime)
class CountDownTimer(Timer):
   r = 0
   def run(self):            
      counter = self.runTime    
      for sec in range(self.runTime):
          time.sleep(1.0)            
          counter -= 1    
        self.r = 1
   def now_it_is():
      return r
def go(t):
   c = CountDownTimer(t)
   c.start()

```

Module II>

```

#! /usr/bin/env python
# -*- coding: utf-8 -*
# -*- Mode: Python -*-
from timerche import go
from timerche import CountDownTimer
odi(5)
while CountDownTimer.now_it_is() == 0:
   print "not now."
else:
   print "Done."

```

Now the proble is, i want to open from the first module, the timer module, and the timer i need to tell the first module when he is done, how can i code that, or if my code from above is ok, i mean the algorythm of it, then what is the error, i think that in timer module, the public var r is always 0, i tried 100 ways, it's still 0.
Any solutions?

---

### Post by pmasiar on 2007-08-31
I might be missing something, not sure what you are trying to accomplish. What is your Python experience, so I will have better idea on what level to answer?

Looks like 'module I' == timerche is your library, and 'module II' is the part containing main() function using it, right?

You imported class, but don't instantiate object of that class. Why bother with OOP if you don't need instances? Just call functions from other modules, and access module-level variables.

Or chances are, I completely misunderstood what are you trying to do.

---

### Post by DamjanDimitrioski on 2007-09-01
The program doesn't have any purpose, i need just to learn how to call a method from another module, but the module is timer, and when the time is up, the timer module to tell the main module that the time is up, and with that result the main module will continue to do what it must do, is this sentence logical, or I have to rewrite it.
P.S> My social skill's are in low level.

---

### Post by pmasiar on 2007-09-01
I assume you just started learning Python, right? Which book do you use? What other (programming) languages you know, if any?

> **DamjanDimitrioski said:**
>  i need just to learn how to call a method from another module, 

So it does not have to be OOP? try plain old procedural approach, in Python you don't use objects and classes unless you **have to** - Python is not Java :-)

```

import modulename
x = modulename.functionname()

```

But of course to have multiple times you better use objects - when you will be ready to do it.

> My social skill's are in low level.

Put them into high level - turbo setting :-)

---

### Post by DamjanDimitrioski on 2007-09-01
What I really need is the main module to control the module, for example, I'm making client and server program, and for the client program I'm making a module to make a fullscreen window, but I need when the main module will send command exit, then the fullscreen module to destroy itself. That is all about.:(

---

