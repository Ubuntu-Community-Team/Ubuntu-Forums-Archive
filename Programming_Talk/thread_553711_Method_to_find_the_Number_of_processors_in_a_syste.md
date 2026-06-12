---
title: "Method to find the Number of processors in a system"
date: 2007-09-18
forum: Programming Talk
---

### Post by murajashekar2003 on 2007-09-18
Warm wishes All,

Is there any other way to find the number of processors of a system.

One way is through   cat /proc/cpuinfo.

**Do we have anyother alternative way?If so how..**

thanks in advance!
Cheers..
Rajasekar

---

### Post by ghostdog74 on 2007-09-18
```

dmesg |grep processor

```

---

### Post by CptPicard on 2007-09-18
[http://www.uwsg.indiana.edu/hypermail/linux/kernel/0204.1/0132.html](http://www.uwsg.indiana.edu/hypermail/linux/kernel/0204.1/0132.html)

Comes up as the very first Google search result for "linux kernel system calls number of processors" ;)

Seems like there are ways to do this in code, but even they parse cpuinfo. So I guess that's your best bet. Although the ...stat...whatever ones look interesting too.

---

### Post by AlexThomson_NZ on 2007-09-18
I have implemented this in a program (check these forums for a benchmarking thread by me).  I used /proc/cpuinfo and it is very robust- be careful about just doing a grep for 'processor' though, as it sometimes appears in (the model name

---

### Post by Lster on 2007-11-26
Hi!

I was just searching through the forums for the same thing! Looking in LibC I found this functionality. I haven't tried it yet but I thought I would post here in case anyone is interested.

[http://www.gnu.org/software/libc/manual/html_node/Processor-Resources.html#Processor-Resources](http://www.gnu.org/software/libc/manual/html_node/Processor-Resources.html#Processor-Resources)

And yes! I do realize this thread is old... ish!

---

