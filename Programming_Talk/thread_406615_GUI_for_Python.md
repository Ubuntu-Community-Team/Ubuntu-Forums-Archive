---
title: "GUI for Python"
date: 2007-04-11
forum: Programming Talk
---

### Post by evagelos on 2007-04-11
Hello 

    I need a Gui for python wx or qy ???

thanks

---

### Post by Jucato on 2007-04-11
I think you meant Qt? There's Eric: [http://www.die-offenbachs.de/detlev/eric.html](http://www.die-offenbachs.de/detlev/eric.html)

It's available in the repositories.

---

### Post by Jussi Kukkonen on 2007-04-11
I suggest you rephrase your question a bit more verbosely. At least I have problems understanding what you need...

---

### Post by nihilocrat on 2007-04-11
wx has better cross-platform support (by that I mean, with Qt, people have to install the Qt libraries) and they will get a native 'look-and-feel'. For the most part, I don't really see a reason NOT to use wx in any GUI project.

---

### Post by ZuLuuuuuu on 2007-04-11
> wx has better cross-platform support (by that I mean, with Qt, people have to install the Qt libraries) and they will get a native 'look-and-feel'. For the most part, I don't really see a reason NOT to use wx in any GUI project.

But if wxPython is used then wxPython libraries and wxWidget libraries should also be installed?

---

### Post by Max_Might on 2007-04-11
Why dont you try PyGTK ... :)

---

### Post by ianare on 2007-04-11
wxPython is open source (less restrictive than LGPL), QT is not OSS for commercial projects.

---

### Post by kikapu on 2007-04-15
> **ianare said:**
> wxPython is open source (less restrictive than LGPL), QT is not OSS for commercial projects.

Qt is under GPL. I had an email conversation with them (Trolltech) and i discussed the subject of Qt lisence in comp.lang.python.
[http://groups.google.com/group/comp.lang.python/browse_thread/thread/5df93d9e9727946f/7099b36de7b6f679#7099b36de7b6f679](http://groups.google.com/group/comp.lang.python/browse_thread/thread/5df93d9e9727946f/7099b36de7b6f679#7099b36de7b6f679)

So, Qt is under GPL and what you can and cannot do falls under the umbrella of GPL.
You can write software with Qt OpenSource Edition and you can sell it. What you have to do is give the source code with your product and clearly state int it that is under GPL too.
Of cource, that way you know beforehand that the person who buy your software can freely give it free to others.

You can also produce software for the company you work for, so i do not think that developing with Qt is a problem any more...
The only reason you will go and but the Commercial Lisence of Qt is if you or your company create "closed source" solutuons, that is, you do not want to give your code to your clients.

---

### Post by pmasiar on 2007-04-15
> **kikapu said:**
> 
The only reason you will go and bu[y] the Commercial Lisence of Qt is if you or your company create "closed source" solut[i]ons, that is, you do not want to give your code to your clients.

IANAL, but LGPL allows to link closed source to it, no? So that is exactly where you would prefer LGPL wxPython?

---

### Post by kikapu on 2007-04-16
> **pmasiar said:**
> IANAL, but LGPL allows to link closed source to it, no? So that is exactly where you would prefer LGPL wxPython?

Xhm...You are correct. I think that building with Qt OS Edition will not allow you to link any other module that is in conflict with GPL. But in Python world, most modules are Open Source too, so there is little chance that problems will arise.
But anyway, you have a point in this.

---

### Post by gh0st on 2007-04-16
> **Max_Might said:**
> Why dont you try PyGTK ... :)

It depends what you want to do but I'd recommend pyGTK as well. It's not right in every situation but I like it :D

---

