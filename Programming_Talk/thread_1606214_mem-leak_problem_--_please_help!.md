---
title: "mem-leak problem -- please help!"
date: 2010-10-26
forum: Programming Talk
---

### Post by Manshtein on 2010-10-26
Hello Dear all!

I have e problem with mem-leak on tomcat6--ubuntu 10.

Mem leak is in servlet, that uses encryption device called WebSentry. Communication with that device is preformed as scenario shown bellow

servlet --> libpkcs11.so --> libwspkcs11d.so --> WebSentry

The mem leak comes from libpkcs11.so library. Unfortunately i can not show you source code of that library, so i am not asking you to solve programming mistakes issue, but for advice.

With pmap i can find address in memory that contains mem-leak garbage. 

Please give me an advice, how can i dump memory exectly at that segment:offset i need to see what actually is in there?

Thank you.

---

### Post by nvteighen on 2010-10-26
> **Manshtein said:**
> Hello Dear all!

I have e problem with mem-leak on tomcat6--ubuntu 10.

Mem leak is in servlet, that uses encryption device called WebSentry. Communication with that device is preformed as scenario shown bellow

servlet --> libpkcs11.so --> libwspkcs11d.so --> WebSentry

The mem leak comes from libpkcs11.so library. Unfortunately i can not show you source code of that library, so i am not asking you to solve programming mistakes issue, but for advice.

With pmap i can find address in memory that contains mem-leak garbage. 

Please give me an advice, how can i dump memory exectly at that segment:offset i need to see what actually is in there?

Thank you.

Steps I'd take:
1) Confirm the leak is not yours by using valgrind. If it is, fix it.
2) Confirm the leak is the library's by searching other people complaints in the web.
3) If nobody has reported this, report it to the library's mantainers.
4) If you know how to fix it, send them a patch. If not, try to give them the most information as possible.

---

### Post by Manshtein on 2010-10-26
Hi!

The problem is, that librarie's developers working in partner's company. We looking for solution together.

Production tomcat with that library dying every 3-th day. Tomcat process becoms 1.3 Gb huge (430Mb on start up). It steals memory every transaction clients do.

If i disable that library to use simple plane text encryption key all working well, but with WebSentry library it dying =((. 

I can not launch that program using valgrind (or i do not any way to do so). It is servlet that starts together with tomcat and runing till out of memory. I need a way to check process.  

Any way thanx for advice.

---

### Post by spjackson on 2010-10-26
> **Manshtein said:**
> Hi!

The problem is, that librarie's developers working in partner's company. We looking for solution together.

Production tomcat with that library dying every 3-th day. Tomcat process becoms 1.3 Gb huge (430Mb on start up). It steals memory every transaction clients do.

If i disable that library to use simple plane text encryption key all working well, but with WebSentry library it dying =((. 

Are you saying that you have isolated the leak to the calls from libwspkcs11d.so to WebSentry? If so, I'd look for API calls that return pointers. Are these documented as requiring to be freed?

In my experience, leaks of large magnitude tend not to be within the internals of a library but at the interface - a leak of large magnitude within WebSentry would soon be known about by many users.

---

### Post by Some Penguin on 2010-10-26
Grab a heap dump with jmap.  Take the heap dump and analyze it w/ e.g. Memory Analysis Tool plugin for Eclipse.

---

### Post by slavik on 2010-10-27
heap dump, along with a stack trace dump, consider adding jmx based monitor for heap utilization.

---

