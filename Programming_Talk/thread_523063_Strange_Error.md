---
title: "Strange Error"
date: 2007-08-11
forum: Programming Talk
---

### Post by DBQ on 2007-08-11
Hey Guys,
  I get this error when I try to run a java jar program.  It worked fine on the other system.  What should I do?

Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
?

---

### Post by nitro_n2o on 2007-08-11
you need to recompile everything i suppose.. 
I'm not sure if there is another thing you can do.. 
But recompiling will solve it

---

### Post by DBQ on 2007-08-11
I tried it, but it did not help.  I think the problem is with java.  Do you have to install some libraries perhaps?

---

### Post by nitro_n2o on 2007-08-12
no it's not Java i'm sure.. that used to happen to me when using eclipse to compile and then using the command line.. classes gets confused :) 
try to delete all class files and compile again... and if you have a Manifest.mf file make sure it doesn't have the java class version (make sure you have a simple manifest file)
And this might happen if you compiled your code using javac 1.6 but run by java 1.5 
check your java stuff versions 
javac -version
java -version
javac must be lower than java, yet better they both be the same

---

