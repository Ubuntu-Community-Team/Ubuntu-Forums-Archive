---
title: "Executor class in Java 5?"
date: 2009-03-07
forum: Programming Talk
---

### Post by andrew222 on 2009-03-07
Does anyone know how we can use the Executor class with threads in Java 5?

---

### Post by kavon89 on 2009-03-07
[QUOTE=Java API]An Executor is normally used instead of explicitly creating threads.[/QUOTE]

I don't think it is meant to be used with Threads.

EDIT: Actually I just noticed its an interface and two other classes with the word Thread in them implement it:

[ThreadPoolExecutor]("http://java.sun.com/javase/6/docs/api/java/util/concurrent/ThreadPoolExecutor.html")

[ScheduledThreadPoolExecutor]("http://http://java.sun.com/javase/6/docs/api/java/util/concurrent/ScheduledThreadPoolExecutor.html")

---

### Post by CptPicard on 2009-03-07
Very broad question... google for examples, there are tutorials. You should also note that Executor is an interface, not a class. You usually use the factory methods in class Executors to build actual implementations of ExecutorService, and then use those to actually execute stuff.

---

### Post by andrew222 on 2009-03-07
OK, I made a mistake and forgot it is an interface.

Thanks a lot CptPicard for the info,  I'll look them up.  I am getting an idea that Executor enables concurrent thread behavior.

---

