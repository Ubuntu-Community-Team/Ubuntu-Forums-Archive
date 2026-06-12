---
title: "using java with pipelining"
date: 2007-01-17
forum: Programming Talk
---

### Post by oco on 2007-01-17
i want to run java with some command like that

echo "A" | java

Here, A is the name of the class.

but it gives an error like that

Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.


anybody has any ideas about that??:confused:

---

### Post by Ramses de Norre on 2007-01-17
Have you got sun's java installed? Because you get errors about gij only..

If not: enable universe and install sun-java5-bin, sun-java5-jdk and sun-java5-jre.

Then run **sudo update-java-alternatives -s java-1.5.0-sun**.

---

