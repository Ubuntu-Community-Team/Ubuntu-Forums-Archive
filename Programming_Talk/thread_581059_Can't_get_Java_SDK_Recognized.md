---
title: "Can't get Java SDK Recognized"
date: 2007-10-19
forum: Programming Talk
---

### Post by iSkylla on 2007-10-19
I can't get the Java SDK to work on my ubuntu distro. I've installed 3 different versions of Java SDK, 5.0, 6.0 and another version that is 1.4 and none of them show up as a compiler in the IDE that I have to use, DrJava. I am running Ubuntu 7.10, any ideas?  I just switched from windows which worked fine and I need to program tonight so if you have any ideas, please, post.

---

### Post by jespdj on 2007-10-19
How did you install those Java SDK's? Try:
```
sudo apt-get install sun-java6-jdk
```
to install Sun's Java 6 SDK. Then you should at least be able to compile and run Java programs from the command line.

I don't know DrJava, so it could also be a problem with that.

---

### Post by iSkylla on 2007-10-19
Yeah, that was the original command that I used.  Could it have possibly installed in the wrong directory?

---

### Post by iSkylla on 2007-10-19
I got it.  I had to manually specify the path to tools.jar.   Thanks for your help though.

---

