---
title: "TCP/IP File Transfer between Win 7 Starter and Ubuntu LTS"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by Jaraqui on 2011-12-20
Dear folks,

   Is there any step-by-step cookbook guide (both sides) to allow me a hughe file transfer between
theese two platforms?

Regards
Jaraqui

---

### Post by jtarin on 2011-12-21
Need some more parameters. Tell us more about the two machines...filesystems, connections.There is a limitation to this type of connection .

---

### Post by heyandy889 on 2011-12-21
My first thought is to try scp from the command line. You can read about it in the manual:

```
man scp
```

Stands for "secure copy."

Anyways, you're gonna do something like

```
scp MyHugeLocalFile.txt heyandy889@http://www.MyAwesomeDestination.org
```

This works if the destination computer is visible, publicly. Like a server. Is one of your computers a server, or publicly accessible through the web?

---

