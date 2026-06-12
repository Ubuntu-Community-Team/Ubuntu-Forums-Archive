---
title: "OS Java and Ubuntu"
date: 2007-05-17
forum: Programming Talk
---

### Post by biffta on 2007-05-17
First off I apoligise if this discussion has already been done had a quick search around and didn't see out. 

So, now that the official Sun java compiler has been available for a while why are we not seeing an official Ubuntu Sun java compiler deb package???

---

### Post by jespdj on 2007-05-17
Sun Java is available in the multiverse repository, look for sun-java6-jdk.

---

### Post by biffta on 2007-05-17
Yeh thanks just installed it. Still needed to accept some strange license though:confused:

---

### Post by steve.horsley on 2007-05-17
I read the otehr day that Sun are still in the process of opening the java source, and that they are havong to re-write some parts that they don't own the rights to. Personally I can't wait. I really liike java and would love to see the OSS community adopt it more.

---

### Post by nickdolan on 2007-05-17
when running swt apps with JDK1.5 or 1.6 under 3d effects I get a blank canvas

anyone know the fix ?

Ta

---

### Post by yatt on 2007-05-17
> **biffta said:**
> Yeh thanks just installed it. Still needed to accept some strange license though:confused:
Java 7 will be released under the GPL. AFAIK, Java 6 will keep whatever license it was released with. Even if I'm wrong, the Java packages haven't been updated since the latest announcements.
> **nickdolan said:**
> when running swt apps with JDK1.5 or 1.6 under 3d effects I get a blank canvas

anyone know the fix ?

Ta
Not use desktop effects and SWT/Swing/AWT. Not very desirable, but that is all there is.

---

