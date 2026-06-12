---
title: "ImportError: No module named libglade"
date: 2006-04-05
forum: Programming Talk
---

### Post by TomG on 2006-04-05
Hi

I created very simple glade and python files but whatever I do I always have a libglade error :

> python test.py
Traceback (most recent call last):
  File "test.py", line 1, in ?
    import libglade
ImportError: No module named libglade

All python packages (python-glade2...), xml packages and libglade2-0 appear installed in Synaptic.
I found tons of posts on forums with this question but no real answer.
What's wrong ? Help Please... :( 

Tom

---

### Post by psychicdragon on 2006-04-05
The python modules for gtk are called gtk and gtk.glade. This is the code you're looking for: ```
import gtk, gtk.glade
```

---

### Post by TomG on 2006-04-05
Thanks for your answer. Will test ASAP.

---

### Post by wolterh on 2009-01-26
Mark as solved if solved please.

---

### Post by bruce89 on 2009-01-26
> **woli said:**
> Mark as solved if solved please.

What, after nearly 3 years?

---

### Post by wolterh on 2009-01-26
Three years later I walked in with that doubt myself, getting away with the uncertainity of if the method worked or not. It costs nothing to mark the thread as solved, please don't troll on me.

---

### Post by bruce89 on 2009-01-26
> **woli said:**
> Three years later I walked in with that doubt myself, getting away with the uncertainity of if the method worked or not. It costs nothing to mark the thread as solved, please don't troll on me.

I amn't trolling, I was just surprised there was such a big bump. Also, threads can't be closed nowadays.

---

### Post by slavik on 2009-01-26
Marked solved!

---

