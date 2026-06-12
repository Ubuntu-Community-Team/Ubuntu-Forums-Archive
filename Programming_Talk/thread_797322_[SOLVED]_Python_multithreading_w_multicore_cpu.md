---
title: "[SOLVED] Python multithreading w multicore cpu"
date: 2008-05-17
forum: Programming Talk
---

### Post by Ux64 on 2008-05-17
Why this program only utilizes one core? Is something in code synchronized? Or can't pyhton utilize multiple cores?

I couln't figure whats wrong with this very simple code.

```

import threading
from time import sleep, time
  
def loop(i, event):
    while not event.isSet():
      cntr = 0
      while cntr < 1000000:
        cntr += 1      
        store='handle some data etc.'
 
event = threading.Event()

print 'starting'
 
th1 = threading.Thread(target=loop, args=(1, event))
th1.start()
th2 = threading.Thread(target=loop, args=(2, event))
th2.start()
th3 = threading.Thread(target=loop, args=(3, event))
th3.start()
th4 = threading.Thread(target=loop, args=(4, event))
th4.start()

#Lisä testi threadit kun testasin 8 threadilla, ei vaikutusta.
#th11 = threading.Thread(target=loop, args=(1, event))
#th11.start()
#th12 = threading.Thread(target=loop, args=(2, event))
#th12.start()
#th13 = threading.Thread(target=loop, args=(3, event))
#th13.start()
#th14 = threading.Thread(target=loop, args=(4, event))
#th14.start() 

print 'running...'

sleep(10)

print 'stop...'

event.set()
 
th1.join()
th2.join()
th3.join()
th4.join()

print 'end'

```

---

### Post by Martin Witte on 2008-05-17
the answer for our issue can be found [here]("http://blog.snaplogic.org/?p=94"), see also [this]("http://www.artima.com/weblogs/viewpost.jsp?thread=214235")

---

### Post by Ux64 on 2008-05-17
Thank you! Excellent answer and helpful and informative links.

It seems that the problem is much worse than I though it would be. It seems that I'll have to do my multi threading programs using Java as I have done earlier.

And I really agree with the first link. There should be easier way than the ways suggested in that link. Because several other languages are doing that just fine.

---

### Post by ricegf on 2008-05-17
> **Ux64 said:**
> It seems that I'll have to do my multi threading programs using Java as I have done earlier.
Perhaps you should try using Jython instead. The GIL exists in the CPython virtual machine, not the language definition; I suspect (but did not verify) that your example would use multiple cores in Jython just fine. It might at least be worth a test.

---

