---
title: "compile java code"
date: 2013-03-24
forum: Packaging and Compiling Programs
---

### Post by shurui91 on 2013-03-24
Hi! I have a simple question here. 

I have a java code which I want to see if there's any difference between using  Oracle JDK and OpenJDK to compile. I installed both of them on my Ubuntu 12.04. I wonder how would I specify which compiler I want to use while I am trying to compile the code? 
Meanwhile, I know the way we check the java version is type in "java -version" in cmd, I wonder if there's a way for us to check the version of OpenJDK. 

Thanks a lot!

---

### Post by solarghost on 2013-03-24
I think the easiest approach would be to just use the direct path of where your java versions are installed. So for example on my machine I would type:

```
 
/usr/lib/jvm/java-6-openjdk/bin/java -version

/usr/lib/jvm/jdk1.7.0_11/bin/java -version

```

The first command would run the open JDK java -version and the second command would run the Oracle java -version

---

### Post by schragge on 2013-03-24
If you install Oracle JDK following the instructions on [uhelp]community/Java[/uhelp], it will use the [Debian alternatives system](http://www.debian-administration.org/articles/91). Then you can change default JDK with
```
sudo update-alternatives --config java
```

---

### Post by shurui91 on 2013-03-26
doesn't seem right on my machine. my oracle version is 1.7.0_17 but this directory doesn't exist.

---

### Post by shurui91 on 2013-03-26
your answer works the best for me. on this page here [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
"Choosing the default Java to use". 
Thank you!

---

