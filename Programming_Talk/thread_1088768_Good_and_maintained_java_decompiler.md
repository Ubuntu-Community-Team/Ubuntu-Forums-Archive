---
title: "Good and maintained java decompiler"
date: 2009-03-06
forum: Programming Talk
---

### Post by azzamite on 2009-03-06
Hi everyone.

I found [_this many_]("http://www.plentyofcode.com/2007/08/java-decompilers-and-obfuscators.html") java decompilers.

So far, my research tells me that **JODE** and **jad** are the most popular.

_But_ the fact is that JODE doesn't seems to have been updated since 2004, so I'm not shure it supports java 6. As for jad, the link to its page doesn't seems to work, so I don't know whether or not it's still being developped.

So my question is:
Is there a decompiler that works with Java 6 (applets) and that is maintained and supported?

---

### Post by drubin on 2009-03-06
I use Jad but this is for mobile j2me.

---

### Post by Winterhart on 2009-03-12
I'm interested in an answer to this, too - all of the links I can find for jad are expired, and it's not part of the Ubuntu repository.

Does anyone know where to find this now, or is there another good (non-orphaned) java decompiler out there?

---

### Post by Ruhe on 2009-03-12
I always use jad (plugins for [IDEA]("http://sourceforge.net/projects/ideajad/") and [Eclipse]("http://jadclipse.sourceforge.net"))
Reason - it does all what I need.

And if you need here is link for webarchive [http://web.archive.org/web/20051001112646/http://kpdus.tripod.com/jad.html](http://web.archive.org/web/20051001112646/http://kpdus.tripod.com/jad.html)

---

### Post by Winterhart on 2009-03-12
Unfortunately the last version of jad seems to dislike me:

[508:laura@alderaan ~/Desktop]$ /home/laura/downloads/jad/jad CreateEmailServiceImpl.class 
/home/laura/downloads/jad/jad: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
[509:laura@alderaan ~/Desktop]$ 

I appreciate it, though!

---

### Post by roccivic on 2009-03-13
> **Winterhart said:**
> Unfortunately the last version of jad seems to dislike me:

[508:laura@alderaan ~/Desktop]$ /home/laura/downloads/jad/jad CreateEmailServiceImpl.class 
/home/laura/downloads/jad/jad: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
[509:laura@alderaan ~/Desktop]$ 

I appreciate it, though!

Sounds like you're missing libc, try:
```
sudo apt-get install build-essential
```

Peace

---

### Post by Winterhart on 2009-03-13
Apt-get keeps telling me to insert the 8.04 CD, which I don't have here, so.. I'll have to wait 'til I get home.  No clue why it won't use the online repositories; just did a trial install of mysql-server for s&g and it downloaded the packages without a hitch.

---

### Post by 1011101 on 2009-04-04
Has anybody been able to use jad on java 1.5 or 1.6? seems like jad version 1.5.8e for linux does not support the newer versions of class files.

---

### Post by ivmai on 2009-12-15
I'd recommend using Jad in conjunction with JadRetro tool (the latter helps Jad with classes of Java 1.4 and 1.5+ formats). It's easy to use (note "-c" option which is required for v1.5.8e):

jadretro -c filename*.class
jad filename.class

PS. It's not integrated into JadClipse at present but it shouldn't be hard to do.

---

### Post by Winterhart on 2010-02-23
Come on, guys - this thread is a YEAR OLD.  Stop resurrecting dead threads!

---

