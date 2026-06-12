---
title: "Eclipse does not support Java Generics?"
date: 2008-01-16
forum: Programming Talk
---

### Post by zchenyu on 2008-01-16
I seem to have a problem with Java generics (as well as other new features to Java 6) in Eclipse. It keeps telling me there is an error, even when I **know** that my code is correct. I know my code is correct because when I compile manually through Terminal, it compiles and runs fine.

Eclipse says in the sidebar as a part of my projects "JRE System Library [java-6-sun-1.6.0.03]". This confuses be because it appears that it is running on the Java 6 JRE.

Any ideas on why this is happening and how to solve this problem?

Oh, and sorry if this thread is in the wrong section.

---

### Post by kevykev on 2008-01-16
Have you got the latest version of eclipse? 

If so, check your project's compiler compliance level is > 5.0. To do this right click on your project and select Properties then Java Compiler and ensure the settings are correct.

---

### Post by zchenyu on 2008-01-16
Heh, thanks
The compiler compliance level was set to 1.4 by default =/

---

