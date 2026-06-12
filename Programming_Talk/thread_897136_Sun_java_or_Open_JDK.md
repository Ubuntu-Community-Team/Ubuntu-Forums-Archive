---
title: "Sun java or Open JDK?"
date: 2008-08-21
forum: Programming Talk
---

### Post by Safder on 2008-08-21
Hello ppl,

I am sure, this question has been asked before, but I am asking it again, since I dont know the answer to the question. What version of java do I use? Do I use the open source version or the sun version? What would be my criteria for using either. Thanks

---

### Post by meanburrito920 on 2008-08-21
In general it is probably better to use the official Sun version. the open source version works fine for 99% of things, but some things break it. It's not perfect.

---

### Post by thomasaaron on 2008-08-25
I'd agree with that. I've noticed that a fair number of commercial java applications that use SWING will not run on well (or sometimes at all) on openjdk. 

Also, many applets will not work at all with it.

In my opinion, as much as I'd *love* to run with openjkd, it's just not that great yet.

---

### Post by howlingmadhowie on 2008-08-25
the openjdk passed the java compatibility test in june 2008. any incompatibilities should be reported as bugs to the developers.

[http://www.jboss.org/feeds/post/java_is_finally_free_and_open](http://www.jboss.org/feeds/post/java_is_finally_free_and_open)

bugs can be reported here: [http://bugs.sun.com/](http://bugs.sun.com/)
the repositiories should contain the newest version.

--------------edit----------------

one of the problems is that java applets can check the version of the java machine being used (by calling System.getProperties().getProperty("java.version")) and refuse to run on a later version. if you see this problem with the openjre1.6 you should see the same behaviour with sun-jre1.6.

---

### Post by henchman on 2008-08-25
I also used the openjdk vm first but experienced slow java programs on a relatively new computer... after switching to the sun package, they were quite faster :)

don't know if that was only me, and be it bug or not: speed matters! :popcorn:

---

