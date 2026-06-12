---
title: "Java paths"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by S.G. on 2008-07-26
To config cmake I have to fill in seveal java paths via ccmake.

* Doubt 1: How comes cmake didn't get them like all the rest? Can it have something to do with the fact that my /usr/java/ directory is empty? What should I put in there and how?

* Doubt 2: What should I put? The requested paths, together with the values I tentatively gave (and that didn't work) are:

//Path to a file.
JAVA_AWT_INCLUDE_PATH:PATH=/usr/lib/jvm/java-6-sun/include

//Path to a library.
JAVA_AWT_LIBRARY:FILEPATH=/usr/lib/jvm/java-6-sun/jre/lib/i386/libawt.so

//Path to a file.
JAVA_INCLUDE_PATH:PATH=/usr/lib/jvm/java-6-sun/include

//Path to a file.
JAVA_INCLUDE_PATH2:PATH=/usr/lib/jvm/java-6-sun/include

//Path to a library.
JAVA_JVM_LIBRARY:FILEPATH=/usr/lib/jvm/java-6-sun/jre/lib/i386/server/libjvm.so

Thank you in advance.

Regards,

S.

---

### Post by jamesstansell on 2008-07-27
Do you have an example of what didn't work?

This is Ubuntu 8.04 LTS, Hardy Heron, right?

---

### Post by S.G. on 2008-07-27
Hello Jamesstansell.

I didn't receive a mail telling me my thread had been answered, so I decided to start a new one explaining things better (after a good night of sleep...).

It is:
[http://ubuntuforums.org/showthread.php?t=871731]("http://ubuntuforums.org/showthread.php?t=871731")

Thanks,

S.

---

