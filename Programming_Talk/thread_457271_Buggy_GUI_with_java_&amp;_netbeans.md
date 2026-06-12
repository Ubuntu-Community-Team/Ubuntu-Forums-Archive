---
title: "Buggy GUI with java &amp; netbeans"
date: 2007-05-28
forum: Programming Talk
---

### Post by hiruzzolo on 2007-05-28
Hi.. I installed Java sdk and netbeans 64 bit for 7.04(64 bit).. The problem is a really buggy gui.. I show you:
[[IMG]http://img46.imageshack.us/img46/7564/schermata1pg8.th.png[/IMG]](http://img46.imageshack.us/my.php?image=schermata1pg8.png)
and if I open the sun java 6 console is the same..Did anyone have this problem? what could I do?

---

### Post by trigun on 2007-05-28
are you using beryl or compiz ?

---

### Post by hiruzzolo on 2007-05-28
I'm using compiz

---

### Post by trigun on 2007-05-29
try this $ export AWT_TOOLKIT=MToolkit

---

### Post by hiruzzolo on 2007-05-29
No.. It's the same..

---

### Post by trigun on 2007-05-29
sorry my bad... i forgot to tell you, that you have to put that in your .bashrc located in your home, and then run netbeans from the terminal.

---

### Post by hiruzzolo on 2007-05-29
If I run netbeans from the terminal It doesn't work neither with .bashrc modified nor like it was before. It gives me this:
```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002ba3e2d8c385, pid=13591, tid=1094965568
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2f385]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid13591.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

---

### Post by hiruzzolo on 2007-06-01
Ok.. I discovered that it is caused by compiz, because if I have Desktop Effects off everything works fine. If I shall know how to resolve this I will post it here.

---

