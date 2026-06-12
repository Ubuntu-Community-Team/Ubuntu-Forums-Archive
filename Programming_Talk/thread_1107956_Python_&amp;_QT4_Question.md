---
title: "Python &amp; QT4 Question"
date: 2009-03-27
forum: Programming Talk
---

### Post by ajackson on 2009-03-27
OK my brain isn't working today (or I'm missing the obvious). Is there a way in python using qt4 to display a window, then (after it has been displayed) fire off a function. If I stick it in something like the __init__ the window won't get displayed until that function has finished (right?) but that function could take a while as it has to fetch a few things from the net.

One way I thought about doing it is emitting a signal that was defined with QueuedConnection but I'm not 100% certain that will do what I am after.

Any help would be appreciated.

---

### Post by maddog39 on 2009-03-27
You need to launch those methods in separate threads so that those methods which fetch things to the internet arent blocking the rest of the application from running. To do this, you can either use the inbuilt python threading class or the QThread class availible in Qt if its availible in PyQt.
 
Python threading documentation:
[http://docs.python.org/library/threading.html](http://docs.python.org/library/threading.html)

---

### Post by fifth on 2009-04-29
I now the thread is 4 weeks old and you've probably got a solution, but my $0.02.

I use a single shot timer at the end of init;

```
QTimer.singleShot(0,  self.doSomeThing)
```

Using a time of zero, essentially adds your function to the event queue which will be processed when the current queue items are finished, ie the window etc has been painted.

I've also tried implementing showEvent() in my objects but it never quite seemed to do what I wanted, it seemed 50/50 whether the function was processed before or after the window was painted.

[Edit]

Just noticed the part about downloading from the internet and time issues, I'd with maddog39's solution and use threads.

---

### Post by ajackson on 2009-04-30
Thanks for that input, I did go down the threads route and it seems to be working fine but the singleshot function is an interesting thing to know.

---

