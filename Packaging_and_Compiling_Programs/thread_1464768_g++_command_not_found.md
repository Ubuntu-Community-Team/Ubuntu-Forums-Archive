---
title: "g++ command not found"
date: 2010-04-28
forum: Packaging and Compiling Programs
---

### Post by gnostlos on 2010-04-28
I cannot compile a little program that has always compiled on other Linux distributions.  The makefile reads:

start: start.o
    g++ -g -o start start.o
start.o: start.c
    g++ -g -c start.c

The response is:

g++ -g -c start.c
make: g++: Command not found

I must have made a very foolish error, for I see no other posts about it.

---

### Post by lisati on 2010-04-28
Try the following and let us know how you get on:
```
sudo apt-get install build-essential g++
```

---

### Post by wojox on 2010-04-28
Did you install:

```
sudo apt-get update; sudo apt-get install build-essential
```

---

### Post by gnostlos on 2010-04-28
Thanks for the amazingly quick reply.  The "apt-get" did install g++.  That solves the problem posed by my post.

---

### Post by ubu.noob.to on 2010-05-26
Thanks a lot [[COLOR=#D40000]**lisati**[/COLOR]]("http://ubuntuforums.org/member.php?u=327635").

---

