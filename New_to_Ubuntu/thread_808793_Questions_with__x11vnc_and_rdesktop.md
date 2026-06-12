---
title: "Questions with  x11vnc and rdesktop"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by ant2ne on 2008-05-26
Using 
[http://ubuntuforums.org/showthread.php?p=236053](http://ubuntuforums.org/showthread.php?p=236053) I got x11vnc to work so that my OLPC can rdesktop into my main "server" computer.

Question 1. How do I get the thing to get its own desktop / login? And not just watching mine.

Question 2. How do I get sound as well as picture through rdesktop?

---

### Post by quelx on 2008-05-27
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by ant2ne on 2008-05-28
> **quelx said:**
> [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
Did that. but that just logs into the current desktop. I want multiple users to be able to log into the server and get their own desktop.

---

### Post by ant2ne on 2008-05-31
nothing? It can't be done?

---

### Post by quelx on 2008-05-31
> **ant2ne said:**
> Did that. but that just logs into the current desktop. I want multiple users to be able to log into the server and get their own desktop.

If you followed those instructions you should have a new X session on display :1, discrete from the :0 you can sit at.

For more displays/users

[http://linuxreviews.org/howtos/xvnc/](http://linuxreviews.org/howtos/xvnc/)

[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

---

