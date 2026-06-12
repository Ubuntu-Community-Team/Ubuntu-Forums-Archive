---
title: "Help with upstart"
date: 2007-12-03
forum: Programming Talk
---

### Post by withus on 2007-12-03
Greetings everyone.

I need to find a way in Ubuntu to run some processes at startup and then respawning them if they die. I know that this used to be done in inittab, but from what i've gathered from reading some info on the web, in Ubuntu one has to use upstart.
I've created a script file to test this, before editing rc-default (i'm not sure if it's gonna be rc-default that i will have to use, but that's another question). In that file i inserted the following code:

```

start on runlevel 2
  
stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

exec /home/pio/test
```


The process starts, but then it gets killed immediately. I've probably made a mess of this "start on" and "stop on", but the truth is that i don't really get the concept of it, and i can't find any good tutorials online. All i find is inittab stuff. If you could give me an example of how to start a process on startup and then keep it alive until the machine gets shutdown (or point me to a good tutorial) i would be very grateful.

Thanks in advance.

---

