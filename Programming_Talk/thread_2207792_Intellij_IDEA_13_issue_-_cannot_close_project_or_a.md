---
title: "Intellij IDEA 13 issue - cannot close project or application"
date: 2014-02-25
forum: Programming Talk
---

### Post by zobayer1 on 2014-02-25
I am using Itellij IDEA 13.0.2 on ubuntu 12.04 64 bit. JVM version is 1.7.0_53 by oracle.

I cannot close the program other than killing java. I am also unable to close opened project. Once a project is open in the IDE then only way to close it is by making the project directory disappear form its current location (by renaming or moving around). and whenever I start the IDE, it loads all the opened projects from last time one by one, and thus takes a long time to be usable. previously I was using IDEA normally, but as best as I remember, these sorts of behavior started showing up after the last auto update.

Are these any kinds of settings issue? looked up it in google and found a similar bug report on jetbrains bug reports section but was for an older version of it. Any help on how to fix the issue will be highly appreciated.
Thanks in advance.

---

### Post by Petaurus on 2014-03-17
in my case (kubuntu 13.10, java version "1.7.0_51" Java(TM) SE Runtime Environment (build 1.7.0_51-b13) Java HotSpot(TM) 64-Bit Server VM (build 24.51-b03, mixed mode), idea 13.0.2) this trouble was **solved by disable android support plugin** (then i successful reopen another project). after this i enable android support plugin.
look at red circle in right bottom of idea interface. i found solution by pressed him.
sorry for pure english:oops:

---

### Post by zobayer1 on 2014-04-13
Honestly, your English is fine. And I do not use android plugin (or hardly any other plugin). I re-installed the program and now it is working fine. The problem caused when I used IDEA's auto update to update to a newer version. Then I downloaded a fresh copy of the newer version and installed it, which seems to have the problem fixed.
Thanks anyway :)

---

