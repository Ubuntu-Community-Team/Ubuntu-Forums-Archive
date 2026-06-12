---
title: "Issue with Java 1.5.0 and 1.6.0"
date: 2009-10-25
forum: Programming Talk
---

### Post by jwbrase on 2009-10-25
I'm not sure if this belongs in this subforum exactly, as it only has indirectly to do with programming (The problem I'm having relates to things I had to install for a programming course, but deals with running Java applications in general), but I wasn't sure exactly which forum it belonged in.

I have several programs on my machine that require Java 1.6.0. I'm also taking a class in which I've been told I should have the 1.5.0 JDK, and nothing earlier or later. But installing the 1.5.0 JDK seems to have messed up the applications I have that use Java 1.6.0, they will no longer run properly, and "java --version" at the CLI reports 1.5.0. Even worse, this behavior has continued even after I removed every package I could find having to do with 1.5.0 and re-installed every package I could find having to with 1.6.0. "java --version" reports 1.5.0 and the programs still fail in the same way even though Java 1.5.0 no longer exists on my system. (There is one program that still runs, which I guess depends on 1.5.0 instead of 1.6.0).

Is there any way to get 1.5.0 and 1.6.0 to play nicely with one another, or, failing that, to get JDK 1.6.0 to compile programs as if it were JDK 1.5.0?

---

### Post by Can+~ on 2009-10-25
/usr/bin/java points to the version of java selected, use:

[PHP]update-java-alternatives -l[/PHP]

To view the current available versions, and then:

[PHP]sudo update-java-alternatives -s <name>[/PHP]

To update to the proper version.

---

