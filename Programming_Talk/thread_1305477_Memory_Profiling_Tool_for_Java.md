---
title: "Memory Profiling Tool for Java"
date: 2009-10-29
forum: Programming Talk
---

### Post by zfranciscus on 2009-10-29
Hi,

I am trying to monitor the memory usage of my java program. As of now I am using 'Top'. Top is a command line tool that shows you the memory usage of your program. The out put is similiar to  the following:

$# top -p <pid>

Output:

PID: <PID>
User: <user>
VIRT: 513M 
%MEM: 25.1

I am trying to find a better memory monitoring tool that can show me what are the java objects that resides in the memory, their size, etc.

Anyone has a suggestion ?



Cheers,

---

### Post by myrtle1908 on 2009-10-30
There are many Java profilers out there, some free some not.  

Have a look at VisualVM ... [https://visualvm.dev.java.net/](https://visualvm.dev.java.net/)

Also some good info here [http://olex.openlogic.com/wazi/2009/how-to-fix-memory-leaks-in-java/](http://olex.openlogic.com/wazi/2009/how-to-fix-memory-leaks-in-java/)

---

### Post by slavik on 2009-10-30
VisualVM/Jconsole, combined with proper verbosegc options. :)

also, there is jstat/jmap

---

### Post by kavon89 on 2009-10-30
NetBeans has a very nice profiler.

---

