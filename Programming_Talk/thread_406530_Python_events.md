---
title: "Python events"
date: 2007-04-11
forum: Programming Talk
---

### Post by Jmccaffrey on 2007-04-11
I am wanting to create an event kernel that tails a log file and throws events based on those parsed from the log in real time.  What is the most pythonic way of implementing this design?  I can think of several ways to accomplish this, but I hope there is some premade event framework that I can use.

---

### Post by skeeterbug on 2007-04-12
> **Jmccaffrey said:**
> I am wanting to create an event kernel that tails a log file and throws events based on those parsed from the log in real time.  What is the most pythonic way of implementing this design?  I can think of several ways to accomplish this, but I hope there is some premade event framework that I can use.

Try the observer design pattern.

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/415310](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/415310)

:D

---

