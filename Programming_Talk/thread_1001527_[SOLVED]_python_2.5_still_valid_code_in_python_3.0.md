---
title: "[SOLVED] python 2.5 still valid code in python 3.0?"
date: 2008-12-04
forum: Programming Talk
---

### Post by aszxcv on 2008-12-04
is it worth learning 2.5 with 3.0 just release?

---

### Post by elbarto_87 on 2008-12-04
I am asking myself the same question. I am taking a python course in a few months, but I doubt that they will be running version 3.0 so I am not sure if I should keep learning with 2.5 or start trying python 3.0

---

### Post by samjh on 2008-12-04
Most Linux distros won't adopt Python 3.0 until later in 2009.

Is it worth learning 2.5?  Well, the changelog doesn't look too extensive.  Most of the changes appear to be syntactic, along with some library changes.

I'd estimate only one or two weeks worth of adjustment for someone already familiar with Python to switch from 2.5 to 3.0.  Given the amount of learning material available for 2.5 (or any 2.x version), I think it's OK to learn 2.5 now and just make adjustments for 3.0 once it becomes more widespread.

Have a look at the differences between 2.5 and 3.0 here:
[http://docs.python.org/dev/3.0/whatsnew/3.0.html](http://docs.python.org/dev/3.0/whatsnew/3.0.html)

---

### Post by Quikee on 2008-12-04
Python 3.0 is still not that much different from Python 2.x. There are some syntax changes, some new stuff and some obsolete or ambiguous stuff removed. However Python 3.0 is still Python - not like a completely new or different language.

---

### Post by gabril on 2008-12-04
Royal institute of Thechnology in Stockholm sweden still teaches python 2.5... (KTH Kungliga Tekniska Högskolan)

Stick to it...

---

### Post by wmcbrine on 2008-12-04
> **samjh said:**
> Most Linux distros won't adopt Python 3.0 until later in 2009.Later *than* 2009, more likely. (If by "adopt", you mean "make their default version of Python".)

The differences aren't huge in terms of learning, but they're enough to break almost every existing Python 2.x program.

---

### Post by pmasiar on 2008-12-04
Learn 2.5 and don't worry. 

Even if 3.0 would be available, most applications will not be switched to 3.0 anytime soon (next 3 years). 2.x Python will be around for quite a while: 2.6 is already out, 2.7 is planned, and possibly more (but there will not be versions beyond 2.9).

Most distros will have 2.6 (for existing apps) and 3.0 (for new) installed in parallel, so there is no reason to worry.

Also, 2.6 allows you to "from __future__ import ..." many features from 3.0, and convert 2.6 code into 3.0 (and warn about tricky areas). 

BTW this question is FAQ every other week, now when LaRoza is not around anymore, can please some mod edit sticky and add link to this discussion?

---

### Post by Qtips on 2008-12-04
BTW this question is FAQ every other week, [/QUOTE] now when LaRoza is not around anymore, can please some mod edit sticky and add link to this discussion?[/QUOTE]

Where is he? It was a great adviser for me !

Thanks

---

### Post by samjh on 2008-12-04
He's still around, but no longer a moderator.

I think Slavik is the moderator who visits here most often now.

---

