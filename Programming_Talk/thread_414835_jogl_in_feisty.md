---
title: "jogl in feisty"
date: 2007-04-20
forum: Programming Talk
---

### Post by zpon on 2007-04-20
Hi
I have just upgraded to feisty, all went reasonably well, but now I can not use jogl any more, has anyone experienced the same problem? Here is the error I get when I run the MainWindow from this "hello world" [http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/code.zip](http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/code.zip)

 ```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x000010cd, pid=7121, tid=3084409744
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  0x000010cd
#
# An error report file with more information is saved as hs_err_pid7121.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

---

### Post by maximk on 2007-04-20
It seems common problem with java in fiesty, not only related to jogl.

Both GUI java apps I use also failed to start (netbean 5.5, oracle-sql-developer).

Netbeans just say:
Segmentation fault (core dumped)

---

### Post by zpon on 2007-04-22
> **maximk said:**
> It seems common problem with java in fiesty, not only related to jogl.

Both GUI java apps I use also failed to start (netbean 5.5, oracle-sql-developer).

Netbeans just say:
Segmentation fault (core dumped)

Okay, do you know of any other threads or if any are working on a solution

---

### Post by JT673 on 2007-04-22
I use JDK 7 (build 1.7.0-ea-b09), and it works fine.  It might be a hardware support issue...

---

### Post by zpon on 2007-04-23
> **JT673 said:**
> I use JDK 7 (build 1.7.0-ea-b09), and it works fine.  It might be a hardware support issue...
Maybe, i just didn't have problem in edgy, my hardware is a macbook (c2d)

---

### Post by SigmundL on 2007-09-18
Azureus, Eclipse, Intellij and other java apps run just fine. But Netbeans crashes with SIGSEGV...

/S

---

