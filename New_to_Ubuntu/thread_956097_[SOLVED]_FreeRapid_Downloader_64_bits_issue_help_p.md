---
title: "[SOLVED] FreeRapid Downloader 64 bits issue? help please."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by evilkastel on 2008-10-22
Hello, all. I got FreeRapid DOwnloader 0.7 and 0.65. Works great but is gives me an error when I add urls. It doesn't matter, because still downloads, but it won't save my URL list, so, i have to copy and paste the links each time I boot. HelP? anyone?

---

### Post by Vity on 2008-10-23
FreeRapid probably doesn't have sufficient write access rights to .FRD folder in your home directory (~/.FRD). Check these rights.

---

### Post by evilkastel on 2008-10-23
Well, I gave bought ~/.FRD and ~/.frd (the folder where I unziped) full permission, and yet it keeps poping this error:

Message:
    java.lang.StackOverflowError
Level:
    SEVERE
Stack Trace:
null
    sun.reflect.GeneratedMethodAccessor2.invoke(Unknown Source)
    sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    java.lang.reflect.Method.invoke(Method.java:616)
    sun.reflect.misc.MethodUtil.invoke(MethodUtil.java:261)
    java.beans.Statement.invoke(Statement.java:231)
    java.beans.Expression.getValue(Expression.java:115)
The rest is quite much like this last four lines with different values. If needed I can post th entire error.
    ----------------------------------------

BTW, are you the same vity who makes it? I love this program, i need to get it to work properly! Please, help!

---

### Post by Vity on 2008-10-23
Hmmms this exception comes from deep inside of Java runtime environment. It has probably nothing to do with FreeRapid. Are you sure you have 1.6 Java correctly installed? Check it with "java -version" command.
Or is it similar to this: [="]http://bugtracker.wordrider.net/task/19?project=4&status[0]=]("http://bugtracker.wordrider.net/task/19?project=4&status[0) ?
XML serialization seems to be broken in Java.

Yeah, I am the same Vity ;-). FreeRapid has own forum here:
[http://wordrider.net/forum/list.php?7]("http://wordrider.net/forum/list.php?7")

---

### Post by evilkastel on 2008-10-23
I was trying to post there, but you were right. I fixed it by reinstalling JRE and uninstalling somethin called OpenJRE or so.... Thank you man for the great app, i love it, way better than USD and suitable for linux.

---

