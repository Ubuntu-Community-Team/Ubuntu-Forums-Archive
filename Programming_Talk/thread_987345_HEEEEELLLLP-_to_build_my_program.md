---
title: "HEEEEELLLLP- to build my program"
date: 2008-11-19
forum: Programming Talk
---

### Post by hoboy on 2008-11-19
I have a cmd file like build.cmd
in  build.cmd cmd file 
I want to call 4 diferent build.xml with ant 
ant build1.xml
ant build2.xml
ant build3.mxl
ant build.xml4
but the problem is that when I run build.cmd only ant build1.xml run not the rest of the ant target, I need a help to do this
 it is a java program

---

### Post by hoboy on 2008-11-19
What I mean is that 
A. Under Execute Windows batch command, I added following:
ant -f build1.xml
ant -f build2.xml
It only runs first build and ignores the second.

I really need all the suggestions

---

### Post by hoboy on 2008-11-20
> **hoboy said:**
> What I mean is that 
A. Under Execute Windows batch command, I added following:
ant -f build1.xml
ant -f build2.xml
It only runs first build and ignores the second.

I really need all the suggestions

anybody out there ?

---

### Post by ufis on 2008-11-20
Generaly people tend to ignore posts with topics like yours. But today I am feeling very helpful.

Have a look at [http://ant.apache.org/manual/CoreTasks/ant.html]("http://ant.apache.org/manual/CoreTasks/ant.html")

---

