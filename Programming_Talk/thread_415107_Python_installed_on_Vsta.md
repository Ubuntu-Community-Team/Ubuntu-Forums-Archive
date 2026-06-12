---
title: "Python installed on Vsta?"
date: 2007-04-20
forum: Programming Talk
---

### Post by LaRoza on 2007-04-20
For all of you out there you like Python, this may be interesting to you.

I know that Python is not pre-installed on Windows, or at least, not XP and earlier versions, but while I was working on my computer with Vista, I typed "python" into the command prompt because I was frustrated with Windows in general and was already in the command prompt. Much to my surprise, the python interpreter, looking the same as on Linux, came up.

It seems it was always there, on Vista anyway.

---

### Post by eentonig on 2007-04-20
Very nice indeed. Now let's just hope M$ doesn't create a MSPython that isn't compatible with the regular one....

---

### Post by barmazal on 2007-04-20
They will impliment anything good from Python or Ruby to C# and Visual Basic on .net 3.0 platform + probably Flash features.  this is what i heard of at least.

---

### Post by pmasiar on 2007-04-20
> **eentonig said:**
> Very nice indeed. Now let's just hope M$ doesn't create a MSPython that isn't compatible with the regular one....

Indeed. 

Chances are that Python in Vista is [http://en.wikipedia.org/wiki/IronPython](http://en.wikipedia.org/wiki/IronPython)  (and [MS project home](http://www.codeplex.com/Wiki/View.aspx?ProjectName=IronPython) ) which for obvious reasons [does](http://www.codeplex.com/IronPython/Wiki/View.aspx?title=Differences&referringTitle=Home) have compatibility problems (it is build on top of .NET) - but it is released under [Shared Source license](http://www.codeplex.com/Project/License.aspx?ProjectName=IronPython) which claims be "open-source compatible" license (but not submitted to OSI).

---

### Post by Lux Perpetua on 2007-04-20
> **LaRoza said:**
> For all of you out there you like Python, this may be interesting to you.

I know that Python is not pre-installed on Windows, or at least, not XP and earlier versions, but while I was working on my computer with Vista, I typed "python" into the command prompt because I was frustrated with Windows in general and was already in the command prompt. Much to my surprise, the python interpreter, looking the same as on Linux, came up.

It seems it was always there, on Vista anyway.I'm not convinced by this account. My XP install (which I never use) came with Python. I was equally surprised to find it, but I'm 99% sure that it was put there by IBM. Who installed Vista on your computer, and how do you know they didn't install Python themselves? 

Also, as others have suggested, I hope you made sure that it really is the familiar Python interpreter.

---

### Post by LaRoza on 2007-04-20
It has all the documentation and is the correct version.

It also has the Python philosophy.

The prompt looks like the same as the one in Linux, but with inversion colors.

I was surprised to find it, I was wondering if anyone with Vista had it also, so I would know for sure where it came from.

---

### Post by Lux Perpetua on 2007-04-20
> **LaRoza said:**
> It has all the documentation and is the correct version.

It also has the Python philosophy.

The prompt looks like the same as the one in Linux, but with inversion colors.

I was surprised to find it, I was wondering if anyone with Vista had it also, so I would know for sure where it came from.Also check where the Python interpreter is in your file hierarchy. If it's not where all the other programs are, it could be a clue. (This is the case in my XP installation.)

---

### Post by AdamG on 2007-04-20
Check out this page:
[http://www.python.org/doc/faq/installed.html](http://www.python.org/doc/faq/installed.html)

Two things:
I would be surprised if it were Microsoft that installed Python rather than the OEM, and
I would be doubly surprised if they installed IronPython instead of CPython. IronPython is like Jython - it's not so much about running Python as it is about running Python in CLR/Java shops, respectively. It wouldn't make sense to run those unless you already had a lot invested in your CLR/Java setup, which newly shipped computers wouldn't.

---

### Post by LaRoza on 2007-04-20
I have a Compaq.

Too bad, I thought it was the best feature of Vista....

---

### Post by pmasiar on 2007-04-20
> **AdamG said:**
> 
I would be doubly surprised if they installed IronPython instead of CPython. IronPython is like Jython - it's not so much about running Python as it is about running Python in CLR/Java shops, respectively. 

AFAIK, MSFT makes effort to make Python (IronPython) "first class citizen" in CLR world. They hired its author, and pay one more developer to work full time on IronPython. They are not stupid, and they work hard to make customers (developers) happy and Windows good development platform. They would be fools not to. 

Support for Python makes sense, dynamic languages is in our future. Sun is building JRuby like that, too.

CPython under Vista obviously does not have access to all cool CLR features (which I  personally do not care about, but some people do), so IronPython *might* be better solution for *some* problems.

Again: I have no idea if Vista installs Python (or IronPython) by default, or someone did it. But from POV of a monopoly, creating popular slightly incompatible version of a popular language like Python just makes sense. If you cannot beat them, join them.

---

### Post by LaRoza on 2007-04-20
Compaq installed it. HP also does that. 

It has nothing to do with Microsoft in this case.

---

