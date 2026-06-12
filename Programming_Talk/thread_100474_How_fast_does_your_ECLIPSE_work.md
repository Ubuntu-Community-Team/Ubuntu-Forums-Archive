---
title: "How fast does your ECLIPSE work?"
date: 2005-12-07
forum: Programming Talk
---

### Post by cyaconi on 2005-12-07
Hi... 
I'm recently swapping from Window$ to ubuntu, and definetively, I won't back again ;) 
I use a lot Eclipse in my notebook and noticed that the performance on windows is really superior. Could be an installation problem (Synaptic)??  or maybe there are some tweaks to apply???

I note the difference principally in the GUI.. for example, on each CTRL-F6, the screen render take at least the double time on ubuntu...

---

### Post by ofek on 2005-12-07
Eclipse is java based and is slow on linux (atleast in all my friends comps and in mine).
I don't think there are tweaks for handling this but if there are, I would like to hear about em too ;)

---

### Post by arpunk on 2005-12-07
It isnt slow if you use the sun java package, try to use it with that and you will get (obviously) a boost in speed and performance. Im using eclipse and so does my wife and its fast, faster than windows, which is why my wife switched to ubuntu.

Heres a copy of my */etc/eclipse/java_home*:
```

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.
/usr/lib/j2sdk1.5-sun

```
Heres my java version:
```

$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
$

```
And eclipse takes less than a second to start up, and it runs pretty well ;)

---

### Post by cyaconi on 2005-12-07
I'll give a try... 

Wich is your workstation configuration (Processor, RAM, etc...)??

[QUOTE=arpunk]It isnt slow if you use the sun java package, try to use it with that and you will get (obviously) a boost in speed and performance. Im using eclipse and so does my wife and its fast, faster than windows, which is why my wife switched to ubuntu.

Heres a copy of my */etc/eclipse/java_home*:
```

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.
/usr/lib/j2sdk1.5-sun

```
Heres my java version:
```

$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
$

```
And eclipse takes less than a second to start up, and it runs pretty well ;)[/QUOTE]

---

### Post by Mike Buksas on 2005-12-08
I noticed a big performance improvement when I switched to Sun's jre also. I'm working on a IBM T23 laptop, with a 1.1GHz Pentium 3 and 640MB of ram, and it's quite usable, even though the startup process is a but slow (about 5 seconds).

[Here's]("http://ubuntuforums.org/showthread.php?t=76754") the HOWTO I followed, by the way. Worked great.

Mike

---

### Post by arpunk on 2005-12-08
[QUOTE=cyaconi]I'll give a try... 

Wich is your workstation configuration (Processor, RAM, etc...)??[/QUOTE]
Intel P4 (SMP kernel) 3ghz, 1gb RAM (dual channeled), 120gb SATA hard drive, Intel Board D865GBF and ATI radeon 9200 256mb.

---

### Post by cyaconi on 2005-12-08
Arpunk, thank you very much... now my eclipse works as expected!!

:) :) :) 

[QUOTE=arpunk]It isnt slow if you use the sun java package, try to use it with that and you will get (obviously) a boost in speed and performance. Im using eclipse and so does my wife and its fast, faster than windows, which is why my wife switched to ubuntu.

Heres a copy of my */etc/eclipse/java_home*:
```

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.
/usr/lib/j2sdk1.5-sun

```
Heres my java version:
```

$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
$

```
And eclipse takes less than a second to start up, and it runs pretty well ;)[/QUOTE]

---

### Post by Jungles on 2006-01-04
Wow, that's fantastic.  Eclipse used to take nearly 40 seconds to start up using GCJ's runtime.  With Sun's JRE, the startup time has halved, and the GUI response is faster too.

Thanks.

[QUOTE=arpunk]It isnt slow if you use the sun java package, try to use it with that and you will get (obviously) a boost in speed and performance. Im using eclipse and so does my wife and its fast, faster than windows, which is why my wife switched to ubuntu.

Heres a copy of my */etc/eclipse/java_home*:
```

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.
/usr/lib/j2sdk1.5-sun

```
Heres my java version:
```

$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
$

```
And eclipse takes less than a second to start up, and it runs pretty well ;)[/QUOTE]

---

### Post by flipkick on 2006-03-01
Indeed, SUN Java Runtime Environment kicks *** ;)

i also followed this howto:
[http://ubuntuforums.org/showthread.php?t=76754](http://ubuntuforums.org/showthread.php?t=76754)


thanks guys ;)

---

### Post by ae+ on 2006-03-24
this has saved me so much anguish!
thanks heaps

---

### Post by tharsan on 2006-03-25
This really helped me as well, thanks for the user who posted that HOWTO on installing Sun's JRE.

---

### Post by Pablasso on 2007-03-18
thanks a lot, i always backed away from eclipse (and aptana and radrails) on ubuntu just because the GUI was choppy, using the sun's JRE solved it all!

---

