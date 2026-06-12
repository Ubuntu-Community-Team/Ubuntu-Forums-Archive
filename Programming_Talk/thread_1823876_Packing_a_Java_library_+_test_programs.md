---
title: "Packing a Java library + test programs"
date: 2011-08-12
forum: Programming Talk
---

### Post by kvv_1986 on 2011-08-12
Hello,

I had to write a small library in Java, and give example programs to test the library. Basically right now I have library.jar and  test_class.java which imports the required classes from library.jar.

All is fine and dandy when I run test_class.java in eclipse, where I can add library.jar to the build path. But when I do "javac test_class.java" with the jar file in the same folder, I get package not found error.

So how do I send over all my code including the test class to someone else?

Thanks.

PS, I would google it, but I am not really sure what to Google for.

---

### Post by ofnuts on 2011-08-13
> **kvv_1986 said:**
> Hello,

I had to write a small library in Java, and give example programs to test the library. Basically right now I have library.jar and  test_class.java which imports the required classes from library.jar.

All is fine and dandy when I run test_class.java in eclipse, where I can add library.jar to the build path. But when I do "javac test_class.java" with the jar file in the same folder, I get package not found error.

So how do I send over all my code including the test class to someone else?

Thanks.

PS, I would google it, but I am not really sure what to Google for.javac is like java, you have to provide a classpath. The current directory is only searched for .class files. If the classes are in a .jar, the jar has to be included in a claspath.

---

