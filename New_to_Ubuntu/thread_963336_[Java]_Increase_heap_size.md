---
title: "[Java] Increase heap size"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Enfer on 2008-10-30
Hi All :)

I would like to know how I can improve java heap size in ubuntu. I know that I have to use the -Xms256mb -Xmx512mb switches, but I don't know where to add them, so java uses this by default.

If anyone could help me, it would be very nice (and if the would, it would only be nicer :p )!

By the way, some data:
Ubuntu 8.04.1
Java version 1.6.0_07

---

### Post by Enfer on 2008-10-30
I'm doing this, because of maven's complains when i try to run a mvn install..

It says:
Embedded error: Error while executing the compiler.
Java heap space

I already tried exporting
JAVA_HOME and JAVA_OPTS, but unfortunately this didn't help :(

I guess also my javac needs more memory.. But it's not easy at all to find where to put it ...

---

### Post by jamesstansell on 2008-11-02
There is probably a mvn variable to set.  The Apache Sling project (in incubation) lists a suggested setting; I'll post what it says the next time I get a chance to rebuild it.

---

### Post by jamesstansell on 2008-11-02
> **jamesstansell said:**
> There is probably a mvn variable to set.  The Apache Sling project (in incubation) lists a suggested setting; I'll post what it says the next time I get a chance to rebuild it.

OK, here is the sling message.

```

     [echo] ********************** WARNING (SLING-443) **********************************
     [echo] On most platforms, building Sling currently requires setting 
     [echo] MAVEN_OPTS="-Xmx256M", see https://issues.apache.org/jira/browse/SLING-443
     [echo] You might get a "java.lang.OutOfMemoryError: Java heap space" if that
     [echo] setting is not correct.
     [echo] *****************************************************************************

```

So try something like this before you run the mvn command.

```

MAVEN_OPTS="-Xmx256M"

```

---

