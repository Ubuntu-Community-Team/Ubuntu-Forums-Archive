---
title: "Java memory usage: Windows vs Linux"
date: 2009-03-22
forum: Programming Talk
---

### Post by samjh on 2009-03-22
I was fiddling around with the latest Netbeans release on both Linux (Debian Lenny) and Windows (XP), when I noticed the HUGE difference in memory usage between the two JVMs.  On Linux, Netbeans was taking up 51MB, while the Windows version was taking up just 30MB.  What's up with the difference?  Is it because the Linux JVM is the server version, while Windows JVM is the client version?  Should there be such a big difference?

---

### Post by slavik on 2009-03-22
there is no difference between 'server' and 'client' version ... the only differences are the options given to it.

another thing is the actual jvm that you are running, are they both from sun? are they both the exact same version? are they both given the exact same options?

20MB difference is not big for Java. most production applications run with 1.5GB/2GB heap size

---

### Post by samjh on 2009-03-22
Both JVMs are Sun's.  v1.6 update 12.

I don't know what options each Netbeans loader passes onto their respective JVMs though.

The difference may not be big in terms of raw numbers, but it is proportionally big.  51MB vs 30MB is a 41% difference!

Frankly, I'm not hugely concerned.  But my curiosity is very much aroused. :)

---

### Post by DocForbin on 2009-03-22
> **slavik said:**
> there is no difference between 'server' and 'client' version ... the only differences are the options given to it.
they are two different binaries. server uses more memory, but unless your windows is 64 bit it should be defaulting to client.

Aside from the other possible differences slavik mentioned, are the projects and netbeans plugins the same?

---

### Post by samjh on 2009-03-22
> **DocForbin said:**
> they are two different binaries. server uses more memory, but unless your windows is 64 bit it should be defaulting to client.

Aside from the other possible differences slavik mentioned, are the projects the same?

I'm talking about just Netbeans with NO files opened, and the same selection of plugins.

My Debian is amd64, while Windows XP is 32-bit.

---

### Post by DocForbin on 2009-03-22
It would be interesting to make an empty java program, and run it on both to compare footprints.

---

### Post by ajgreeny on 2009-03-22
That is the difference, surely.  A 64 bit OS needs and uses more memory than a 32 bit OS for the same application in their corresponding bit  types.

---

### Post by slavik on 2009-03-23
java -jar blah.jat -Xms 2048 -Xmx 2048

there, 2GB of heap. :)

---

### Post by samjh on 2009-03-23
> **DocForbin said:**
> It would be interesting to make an empty java program, and run it on both to compare footprints.

I haven't made an empty Java program, but I cooked up a little "hello world" Swing program which takes up 22.3MB on Lenny 64bit, and 17.8MB on WinXP 32bit.  Not such a big difference (20%).

---

### Post by any.linux12 on 2009-03-23
> **ajgreeny said:**
> That is the difference, surely.  A 64 bit OS needs and uses more memory than a 32 bit OS for the same application in their corresponding bit  types.

********

---

