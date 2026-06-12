---
title: "Eclipse tends to hang around even after closing"
date: 2006-06-06
forum: Programming Talk
---

### Post by jvictor on 2006-06-06
Hi,
Im using the sun java from multiverse and am running eclipse 3.1 from eclipse.org

I find that even after I exit eclipse the java process still keeps running. 

Before running eclipse

~$ ps -el | grep java
~$ 

While running eclipse

$ ps -el | grep java
0 S  1000 17560 17559 49  75   0 - 128710 stext ?        00:00:06 java

After clsing eclipse
~$ ps -el | grep java
0 S  1000 17560 17559 10  75   0 - 125870 322459 ?       00:00:08 java


Looks like System.exit(0) is not written for the windowClosing event ;)

Any workarounds ? I'm gng to try 3.2 tomo, and see if it happens on 3.2 too

****EDIT****
Eclipse 3.2 too behaves in the same way !!

****EDIT*****
Reported as a bug at eclipse-bugzilla

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=145687](https://bugs.eclipse.org/bugs/show_bug.cgi?id=145687)

---

