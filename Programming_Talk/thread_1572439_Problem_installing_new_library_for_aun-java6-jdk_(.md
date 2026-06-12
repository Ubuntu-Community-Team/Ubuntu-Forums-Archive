---
title: "Problem installing new library for aun-java6-jdk (Please somebody help)"
date: 2010-09-11
forum: Programming Talk
---

### Post by prince.k94 on 2010-09-11
I have added libjson-java library on ubuntu 10.04 but jar files are not automatically included in classpath. Why is it so? I have sun-java6-jre and sun java6-jdk installed on my computer. And i don't know where the classpath settings are saved. I want those jar files to be permanently included in the classpath so that i don't have to add those to command line every time i compile or run programs.

---

### Post by GregBrannon on 2010-09-11
To add the contents of a .jar file into your classpath you need to specify that file in the classpath ...

```
export CLASSPATH=$CLASSPATH&#58;/path/to/jarfile.jar
```

---

### Post by prince.k94 on 2010-09-11
Thanks. But, do I have to add path of even those packages which I have added from ubuntu repository?
Also these is no previous class path setting in /etc/environment. So where are the classpath settings?

---

### Post by prince.k94 on 2010-09-11
Also it did not work. I manually included classpath for libjson-java during compile time but it did not work. Is sun-java6 is not compatible with libjson-java library?

---

### Post by Some Penguin on 2010-09-11
You didn't actually do any searching, e.g. for "configuring Java classpath", did you?

[http://download.oracle.com/javase/tutorial/essential/environment/paths.html](http://download.oracle.com/javase/tutorial/essential/environment/paths.html)

---

### Post by GregBrannon on 2010-09-11
One of the mistakes I continually make when trying to help someone is accepting that they know (1) what the problem is, and (2) what will solve #1.  I trust their diagnosis and answer their question on how to accomplish #2 to fix #1.  I learn over and over again (but I'm slow) that the OP doesn't always know what's really wrong or how to fix it.

So, rather than continuing with those lousy assumptions, please tell us why you believe the library you "added" is not working.  Provide as much detail as possible.  How did you add it?  (You already suggested you added it from the repository, but confirm.)  How have you tried to use it since you added it?  What happened after you tried to use that made you believe something was wrong?  Provide code, exact error messages, as much detail as possible.

Sorry for the false start and thanks for your patience.

---

