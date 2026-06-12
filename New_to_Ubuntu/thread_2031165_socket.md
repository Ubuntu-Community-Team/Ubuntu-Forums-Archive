---
title: "socket?"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by smemamian on 2012-07-21
hi

What is the output of this command ?

```
find -type s
``````
./.cache/gnome-system-monitor.sm-emamian.2987582767
```
tnx

---

### Post by smemamian on 2012-07-23
up:(

---

### Post by codemaniac on 2012-07-23
> **smemamian said:**
> hi

What is the output of this command ?

```
find -type s
``````
./.cache/gnome-system-monitor.sm-emamian.2987582767
```
tnx

```
find -type s
```
Find only the socket files.

below are the other options supported by find's -type qwitch .

> b
block (buffered) special
c
character (unbuffered) special
d
directory
p
named pipe (FIFO)
f
regular file
l
symbolic link
s
socket
D
door (Solaris)

---

