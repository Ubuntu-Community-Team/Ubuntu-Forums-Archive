---
title: "Sun-Java 6.26-1 update causes ram shortage"
date: 2011-07-21
forum: Programming Talk
---

### Post by capoocan on 2011-07-21
Hello all,

since the recent update of the java-package from Sun (6.26-1lucid1 on 10.04LTS) about  a week ago, we experience an extreme memory consumption when running any java application (e.g. eclipse). The JVM seems to ignore the maximum memory parameter and the resident set size goes up to gigabytes of RAM, which causes the overall performance of the system to drop dramatically.

Using the openjdk java version is not an alternative, since we find it to be unstable - eclipse sporadically just "disappears" from the screen.

Did anyone encounter similiar effects?

Has anyone a hint what to do about it?

Thanks a lot,
Udo.

---

### Post by t1497f35 on 2011-07-21
Does downloading the almost final version of the soon to be released jdk7 [from here]("http://jdk7.java.net/download.html") not solve your issue?
If so, I'd highly suggest reporting it as a bug.

---

