---
title: "Java driving me crazy!"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by tuxxes on 2012-08-23
Hello gentlemen I am having an issue with Java and have been for days now. I am trying to run a .jar program (obviously) and nothing happends. However when I run java -jar jarfile.jar I get this print out. UnsupportedClassVersionError: project1/MainProject : Unsupported major.minor version 51.0.

I have tried uninstalling openJDK6 and reinstalling. I have tried installing openJDK7 with and without JDK6. I have tried oasisJAVA 7u5. Nothing has worked for me so far. Thank you for the future efforts.

---

### Post by spjackson on 2012-08-23
As I understand it, " Unsupported major.minor version 51.0" means that the jar was compiled with Java 7 and you are attempting to run it with an earlier JDK, presumably 6.

If you have a Java 7 JDK installed and
```
java -version
```shows 1.7something, then
```
 java -jar jarfile.jar
```should work, but if ```
java -version
```does not show 1.7something, then the jar won't work.

If it doesn't work with a Java 7 JDK, then post the version string (using the above command). Is the jar downloadable from somewhere? Does it come with any requirement instructions?

---

