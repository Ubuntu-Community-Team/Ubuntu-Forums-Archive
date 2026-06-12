---
title: "C++ : how to run a function and main program simultaneously?"
date: 2010-04-26
forum: Programming Talk
---

### Post by perham on 2010-04-26
well, the title describes it. all I want to do is to run a function while my program is running simultaneously. should I create another thread for that? and if I create another thread, can I access my data in the main program?

any idea in which ways I can do this, and which is simpler to learn?

thanks in advance

---

### Post by mmix on 2010-04-26
[https://computing.llnl.gov/tutorials/pthreads/](https://computing.llnl.gov/tutorials/pthreads/)

---

### Post by dragos2 on 2010-04-26
Use threads. But it sounds like your design is bad.

---

### Post by MadCow108 on 2010-04-26
have a good look at the post provided by mmix

and then "forget" it and use boost threads ;) (or any other c++ thread implementation)
boost threads are a lot easier to handle than raw pthreads:
[http://www.boost.org/doc/libs/1_42_0/doc/html/thread.html](http://www.boost.org/doc/libs/1_42_0/doc/html/thread.html)
their also very similar to the threads proposed in the upcoming new standard, so no waste to learn them now.

---

### Post by doomguard88 on 2010-04-26
Well you can use the Qt framework to write a multitreaded programm.

Qt is a complete framework for developing gui and network capable applications 
 which also be compiled for every platform with no changes.

Check the link below if you are interested. :)


[http://doc.qt.nokia.com/4.6/threads.html]("http://doc.qt.nokia.com/4.6/threads.html")

[http://qt.nokia.com/support]("http://qt.nokia.com/support")

---

### Post by perham on 2010-04-26
> **mmix said:**
> [https://computing.llnl.gov/tutorials/pthreads/](https://computing.llnl.gov/tutorials/pthreads/)

> **MadCow108 said:**
> have a good look at the post provided by mmix

and then "forget" it and use boost threads ;) (or any other c++ thread implementation)
boost threads are a lot easier to handle than raw pthreads:
[http://www.boost.org/doc/libs/1_42_0/doc/html/thread.html](http://www.boost.org/doc/libs/1_42_0/doc/html/thread.html)
their also very similar to the threads proposed in the upcoming new standard, so no waste to learn them now.

thanks. I look into them.

---

### Post by perham on 2010-04-26
> **dragos2 said:**
> Use threads. But it sounds like your design is bad.



> **doomguard88 said:**
> Well you can use the Qt framework to write a multitreaded programm.

Qt is a complete framework for developing gui and network capable applications 
 which also be compiled for every platform with no changes.

Check the link below if you are interested. :)


[http://doc.qt.nokia.com/4.6/threads.html]("http://doc.qt.nokia.com/4.6/threads.html")

[http://qt.nokia.com/support]("http://qt.nokia.com/support")

thanks for the links. the problem is that I'm modifying a program already written using GTK, and implementing QT now is quite hard, and I have to either use the same design or rewrite huge parts of the code.

---

### Post by doomguard88 on 2010-04-26
Well you are right re-writing the whole thing isn't an option.
You are better off with GTK.

If you come to a dead-end check out Qt i find its documentation much better and easier to follow.

Good luck.

---

