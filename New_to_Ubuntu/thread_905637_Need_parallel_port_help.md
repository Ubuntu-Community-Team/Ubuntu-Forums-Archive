---
title: "Need parallel port help"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by chriscross93 on 2008-08-30
I need to give a program (parashell) direct access to my parallel port.  I have been searching/working on it all day, but to no avail.  Any help or suggestions would be greatly appreciated!

---

### Post by cariboo on 2008-08-30
Have you got the parallel port modules installed? In a terminal type:

```
lsmod | grep para*
```

your out put should be something like this:

```
 lsmod | grep para*
parport_pc             44200  1 
parport                50096  3 ppdev,lp,parport_pc
```

To find your parallel ports address, in a terminal:

```
cat /proc/ioports
```

Look for paraport0

Jim

---

### Post by chriscross93 on 2008-08-30
First, sorry about the double post.  I wasn't surre which one it belonged in.  Second, when I run that code in th terminal, I dont get an output.

---

