---
title: "sun java/openjdk"
date: 2008-11-10
forum: Packaging and Compiling Programs
---

### Post by talonstriker on 2008-11-10
Anyone know if java.util.Scanner is implemented by openjdk?  For some reason, my program using that class isn't compiling because Eclipse can't find that class.  Looking at the "system library," I notice that java.util.Scanner isn't there.  

edit: Just downloaded the Sun's version and I am still getting that error.
```

rdeva@sinusoidal:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)

```

edit: If I call the javac manually, the file compiles like a charm.  Looks like a eclipse problem.

Solved:  Looks like I had several outdated VM's that weren't uninstalled by Synaptic.  Just had to change the library.  
I'll leave this so it may be of help to someone in the future.

---

