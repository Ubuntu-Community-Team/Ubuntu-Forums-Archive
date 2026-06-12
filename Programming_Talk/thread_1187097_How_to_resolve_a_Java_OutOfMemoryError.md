---
title: "How to resolve a Java OutOfMemoryError?"
date: 2009-06-14
forum: Programming Talk
---

### Post by rmnproject on 2009-06-14
As I understand, the error occurs because the java heap space keeps getting exhausted.So i need to increase the heap space size. The problem is, i don't really know how much heap space my program requires(I hope that doesn't sound too stupid)!The application is a Java3D application and one module in it does infact require a lot of memory(which is where i'm getting the error),but i'm not sure exactly how to track the memory heap requirements there. is there some way to track this? I'm using NetBeans. Does anybody know if NB has some Java3D specific feature to monitor n handle this problem (or maybe even some way to track n handle the memory burn so as to reduce the memory requirement itself- the application is a little complex so it will take way too long to manually figure that out )?

---

### Post by jespdj on 2009-06-14
You could try using JConsole, a monitoring tool included with Sun Java 6. Run the command "jconsole" from a terminal, connect to your running application and watch it.

You can give your program more heap space by specifying the -Xmx option on the command line, for example:
```
java -Xmx1024m com.mypackage.MyProgram
```
This would give your program max. 1024 MB memory (1 GB) to work with.

---

