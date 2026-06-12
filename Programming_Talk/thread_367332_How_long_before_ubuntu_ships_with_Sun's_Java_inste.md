---
title: "How long before ubuntu ships with Sun's Java instead of gij??"
date: 2007-02-22
forum: Programming Talk
---

### Post by laxmanb on 2007-02-22
Sun open sourced Java a while back... how long before the free linux distros come bundled with Java instead of GNU Classpath?? 

also, what is the performance differential between gij and java(sun)??

---

### Post by Jussi Kukkonen on 2007-02-22
A small correction: Sun announced they'd open source Java a while back.

I imagine it'll be packaged after they are done with the opening -- which by Suns original account should mostly be ready by summer.

---

### Post by samjh on 2007-02-22
> **laxmanb said:**
> Sun open sourced Java a while back... how long before the free linux distros come bundled with Java instead of GNU Classpath?? 

also, what is the performance differential between gij and java(sun)??

At the moment only the JVM, javac compiler, Java ME framework, and Java EE framework are open-sourced.

The full JDK SE will not be open sourced under the problems of open-sourcing encumbered code (especially Java 2D) are solved.

As for performance, Sun's JVM for servers perform much better than GCJ, but Sun's client JVM and GCJ perform similarly to each other.

---

