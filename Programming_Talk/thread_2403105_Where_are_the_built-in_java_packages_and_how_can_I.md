---
title: "Where are the built-in java packages and how can I view them?"
date: 2018-10-07
forum: Programming Talk
---

### Post by MaindotC on 2018-10-07
I'm following a book exercise on creating a clock program. In the program I call import java.time.* and java.time.temporal.*.  How can I view all the classes offered by these imports?  I'm expecting to see entries for LocalDateTime.now and now.get(ChronoField.*)  Apologies if my terminologies are incorrect - just beginning.

---

### Post by spjackson on 2018-10-08
In the documentation. e.g. for java.time [https://docs.oracle.com/javase/8/docs/api/java/time/package-summary.html](https://docs.oracle.com/javase/8/docs/api/java/time/package-summary.html) and for java.time.temporal [https://docs.oracle.com/javase/8/docs/api/java/time/temporal/Temporal.html](https://docs.oracle.com/javase/8/docs/api/java/time/temporal/Temporal.html)

---

### Post by MaindotC on 2018-10-09
> **spjackson said:**
> In the documentation. e.g. for java.time [https://docs.oracle.com/javase/8/docs/api/java/time/package-summary.html](https://docs.oracle.com/javase/8/docs/api/java/time/package-summary.html) and for java.time.temporal [https://docs.oracle.com/javase/8/docs/api/java/time/temporal/Temporal.html](https://docs.oracle.com/javase/8/docs/api/java/time/temporal/Temporal.html)

Thanks but I was wondering how I'd view the code in the package, not information about the package.  If I make a package in Eclipse it has a hierarchy displayed on the package explorer usually on the left side.  I can see this for packages I create as part of exercises I'm conducting. How would I look at packages that come with the JDK?

---

### Post by spjackson on 2018-10-10
[https://dzone.com/articles/attaching-java-source-eclipse](https://dzone.com/articles/attaching-java-source-eclipse)

---

