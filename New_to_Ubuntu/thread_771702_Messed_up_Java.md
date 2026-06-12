---
title: "Messed up Java"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ebeckhusen on 2008-04-27
I was trying to get Java to work in FireFox 2, with no luck, so I reinstalled Firefox 3.  Now Java works, but only half-way.  When I try to run a game on Pogo the game window opens, but then it quits out and the window closes.

In trying to fix Java, I had made some symbolic links and I was wondering if maybe that was the problem.  So how can I find the links and find out if they're broken, or how can I find and remove them altogether?

---

### Post by daimaru on 2008-04-27
try using different java version isssue this command and select a version:
```
sudo update-alternatives --config java
```

---

### Post by ebeckhusen on 2008-04-27
I think I might have solved it.  It appears to have been a problem with the ubuntu firefox extensions.  I disabled them and now Pogo works fine.

---

### Post by ebeckhusen on 2008-04-28
Okay, so I didn't quite solve it.  It seems like a java process keeps running after I close my Pogo window.  If I go in and end the process, I can get the games to run again.    So, how do I fix it so that the java process will terminate correctly?  (I'm still relatively new, so if you need any logs or anything let me know, and let me know how to get them for you).

---

