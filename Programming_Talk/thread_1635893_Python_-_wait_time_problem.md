---
title: "Python - wait time problem"
date: 2010-12-02
forum: Programming Talk
---

### Post by Dragice on 2010-12-02
Hey, I've been working on a project for a while now. What it does is, it reads data from a website every five minutes, then updates itself. Thing is, I'm having a little trouble getting it to wait five minutes. This is what I have been using in python:

```
x = 1
        while x == 1:
            self.get_data
            time.sleep(300)
```

It's a tkinter application I'm running this through basically, but that's what I was doing to get it to go every 5 minutes. Unfortunately, whenever I do, I get the error: 
"AttributeError: 'str' object has no attribute 'sleep'"
Which makes no sense to me, because I'm importing from the time module.

---

### Post by DaithiF on 2010-12-02
at some point you must have assigned a string variable to time, so that you've lost the reference to the time module.

search your code for something like:
time = ??something??

---

### Post by Dragice on 2010-12-02
Ah, turns out I had by accident. Thanks mate!

Although, now the tkinter window isn't opening. Oh dear.

---

