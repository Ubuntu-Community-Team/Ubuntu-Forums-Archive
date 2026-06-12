---
title: "Configuring command line to be used in Eclipse IDE"
date: 2012-01-20
forum: Programming Talk
---

### Post by alfa_80 on 2012-01-20
I need a help from those who are familiar with developing software using Eclipse IDE. Currently, I am using a command like like below:

```
 g++ -Wall -I/usr/include/boost/ try_boost.cpp -lboost_thread -L/usr/share/lintian/overrides/libboost-thread1.40.0 -o try_boost
``` 

How do I configure in the Eclipse by copying and pasting the above command line so that I do not need to use command line and proceed with CTRL-B and CTRL-F11 using Eclipse (I mean just using GUI-based). How could I do that?

Thanks in advance.

---

### Post by r-senior on 2012-01-21
I only use Eclipse for Java, but command line arguments are usually added in Run Configurations. The little arrow next to the run button in the toolbar should bring up a menu that takes you there.

---

