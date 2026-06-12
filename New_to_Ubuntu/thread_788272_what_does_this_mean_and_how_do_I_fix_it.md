---
title: "what does this mean and how do I fix it?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by valke on 2008-05-09
Hi all, I'm using the Dell wiki to get my sound fixed. When entering code into the terminal, I get this error:

```
downdrift@dell-desktop:~$ sudo dpkg -r hsfmodem
dpkg: status database area is locked by another process
```

---

### Post by hotchkikr on 2008-05-09
you already have a package manager running (probably an updater)

you can't run 2 package managers at the same time

there is nothing wrong, you'll just have to wait

---

### Post by kpkeerthi on 2008-05-09
Do you have Synaptic or aptitude/apt-get command running when you entered this command?
Close Synaptic or wait till apt-get finishes and then run this command.

---

