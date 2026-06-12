---
title: "Why linux won't let my java program to use all cpus?"
date: 2013-05-04
forum: Programming Talk
---

### Post by AADAS on 2013-05-04
Why linux won't let my java program to use all cpus?

---

### Post by Zugzwang on 2013-05-04
Can you provide us with a minimal working example that shows the issue?

Using more than one core at a time is supported by the JVM, so it should work. Did you split the computation-heavy task that you are trying to perform into multiple threads? This is a requirement for using more than one cpu. If you do use multiple threads already, are there probably any locks in your program that prevent the threads from actively running in parallel?

At the very least, the garbage collector is multi-threaded. So even if your program does not use multiple threads, the garbage collector will use more than one cpu at a time.

---

### Post by slickymaster on 2013-05-06
Are you using threads just now? Where is the data coming from and going to?
If your program is single-threaded, then no number of cores on your machine is going to make it run any faster. Without using multiple threads or processes (or something other than the one process running), you won't be able to achieve n*100% usage on a n-core machine.
Java does have threading support, but it won't automatically parallelize your code for you. Another important detail to note is that Java threads are not the same as system threads. The JVM often has its own thread scheduler that tries to put Java threads onto actual system threads in a way that's fair, but there's no actual guarantee that it will do so.
Check [this javadoc]("http://docs.oracle.com/javase/1.4.2/docs/api/java/lang/Thread.html").

---

