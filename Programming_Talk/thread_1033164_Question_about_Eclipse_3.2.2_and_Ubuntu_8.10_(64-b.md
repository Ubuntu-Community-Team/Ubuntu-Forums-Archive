---
title: "Question about Eclipse 3.2.2 and Ubuntu 8.10 (64-bit)"
date: 2009-01-07
forum: Programming Talk
---

### Post by tomdkat on 2009-01-07
So, I installed Eclipse 3.2.2 on Ubuntu 8.10 using the Synaptic Package Manager.  The installation went fine and Eclipse runs just fine.

I've installed Subclipse because I need to access a SVN repository over SSH.  During the process of getting this working, I discovered Eclipse isn't using the "eclipse.ini" file in the /usr/lib/eclipse directory.

In fact, I can't find which configuration file it's using.  I need to get JavaHL running and I need to specify the path to the JavaHL shared libraries.

Which config file does the Ubuntu Eclipse package use?

Thanks!

Peace...

---

### Post by borobudur on 2009-03-21
That's what worked on my 64bit laptop under Intrepid:

[LIST=1]
[*]installed the binding library:* libsvn-java*
[*]added this vm argument to the *eclipse.ini* file: (after -vmargs) ```
 -Djava.library.path=/usr/lib/jni
```
[*]starting eclipse with telling which jre to use: ```
/usr/lib/eclipse/eclipse -vm=/usr/lib/jvm/java-6-sun-1.6.0.10/jre/bin/java
```
[/LIST]

---

