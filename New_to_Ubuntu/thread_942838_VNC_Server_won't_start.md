---
title: "VNC Server won't start"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Jamina1 on 2008-10-09
I have xubuntu running on a "headless" machine and about a month ago is the last time I needed to log on to do anything to it.

Today, i try to start firefox inside the vnc server and it fails.
I tried some other programs too and they don't work either. What gives?

```
administrator@lamp:~$ tightvncserver

New 'X' desktop is lamp:1

Starting applications specified in /home/administrator/.vnc/xstartup
Log file is /home/administrator/.vnc/lamp:1.log

administrator@lamp:~$ firefox -display lamp:1
Error: no display specified

```

---

### Post by Nxion on 2008-10-09
> **Jamina1 said:**
> I have xubuntu running on a "headless" machine and about a month ago is the last time I needed to log on to do anything to it.

Today, i try to start firefox inside the vnc server and it fails.
I tried some other programs too and they don't work either. What gives?

```
administrator@lamp:~$ tightvncserver

New 'X' desktop is lamp:1

Starting applications specified in /home/administrator/.vnc/xstartup
Log file is /home/administrator/.vnc/lamp:1.log

administrator@lamp:~$ firefox -display lamp:1
Error: no display specified

```


Has this setup work in the past? trying to open Firefox this way?

---

