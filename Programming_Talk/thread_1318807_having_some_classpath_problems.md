---
title: "having some classpath problems"
date: 2009-11-07
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2009-11-07
Hey All

I'm trying to package a java app I'm writing in netbeans.  It runs from within the directory that netbeans built it in, but if I move it somewhere else, I get this error:
Exception in thread "main" java.lang.NoClassDefFoundError: org/jdesktop/application/SingleFrameApplication

I've added both swing libraries available in netbeans to the compilation and run paths and messed with the manifest file a bit, but nothing has any effect.  

Does anyone know how to fix this so that I can run this jar file independent of the location?  
Thanks a lot.

---

