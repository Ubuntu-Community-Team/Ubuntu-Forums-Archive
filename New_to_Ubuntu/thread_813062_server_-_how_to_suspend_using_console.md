---
title: "server - how to suspend using console"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by vashwood on 2008-05-30
I know how to have the computer suspend from the options in GDM.  But how do I set it up in the console if I don't use GDM?

---

### Post by quelx on 2008-05-30
[http://ubuntuforums.org/showthread.php?t=591036](http://ubuntuforums.org/showthread.php?t=591036)

---

### Post by bluefrog on 2008-05-30
you would have a look at apmd I presume but a server is not supposed to go off line.

---

### Post by Oldsoldier2003 on 2008-05-30
> **bluefrog said:**
> you would have a look at apmd I presume **but a server is not supposed to go off line**.

thats what caught my attention in the topic subject :)

---

### Post by vashwood on 2008-05-30
hahaha...yeah.  But I want to save on my PGE bill so I'm going to have my server go to sleep and when I want to use it I'll just have a computer send a magic packet to wake it up.

---

### Post by mikitz on 2009-02-14
In many cases it makes sense for servers to go to sleep and then wake up when something tries to connect.

---

### Post by ssam on 2009-06-15
found this post via a google search. this page may be useful [http://blog.dustinkirkland.com/2009/02/ubuntu-server-suspendhibernateresume.html](http://blog.dustinkirkland.com/2009/02/ubuntu-server-suspendhibernateresume.html)

the ubuntu server devs think suspending servers is good. the page recommends using

```
sudo pm-suspend
```
or
```
pm-hibernate
```

it also has instructions for wake on lan

---

