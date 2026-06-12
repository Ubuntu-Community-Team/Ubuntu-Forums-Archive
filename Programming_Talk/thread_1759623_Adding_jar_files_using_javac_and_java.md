---
title: "Adding jar files using javac and java"
date: 2011-05-15
forum: Programming Talk
---

### Post by guest_user on 2011-05-15
I need to link in a jar file, the command I used to do this is 
javac Test.java -cp /path/to/jar/file
and it compiles ok however, when I try to run 
java Test
it gives me 

Caused by: java.lang.ClassNotFoundException: javax.mail.Session
        at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
        ... 1 more

what should is the actual command?

---

### Post by myrtle1908 on 2011-05-16
You still need to tell Java where the libs are at runtime.  Add the -cp switch like you did when compiling eg.

```
java -cp /path/to/jar/file Test
```

---

### Post by guest_user on 2011-05-16
> **myrtle1908 said:**
> You still need to tell Java where the libs are at runtime.  Add the -cp switch like you did when compiling eg.

```
java -cp /path/to/jar/file Test
```

java -cp ~/Libraries/javamail-1.4.4/mail.jar Main

that was what I typed but it gave me this:
Exception in thread "main" java.lang.NoClassDefFoundError: Main
Caused by: java.lang.ClassNotFoundException: Main
        at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: Main.  Program will exit.

---

### Post by myrtle1908 on 2011-05-16
Is your class named Main?  The error suggests it is not ... or java cannot find a class named Main in your classpath.

Are you running the command from the directory where Main.class is found?

---

### Post by guest_user on 2011-05-16
> **myrtle1908 said:**
> Is your class named Main?  The error suggests it is not ... or java cannot find a class named Main in your classpath.

Are you running the command from the directory where Main.class is found?


ok I added an extra :. for the -cp option and it worked but I have another problem, 

Ini.java:9: package com.test.utils does not exist
import com.test.utils.*;

What is the cause of this issue?
My .java file isn't in a hierarchy of folders like /com/test/utils/ etc, is it a problem?

---

### Post by bwanamarko on 2011-12-31
> **guest_user said:**
> ok I added an extra :. for the -cp option and it worked but I have another problem, 

Ini.java:9: package com.test.utils does not exist
import com.test.utils.*;

What is the cause of this issue?
My .java file isn't in a hierarchy of folders like /com/test/utils/ etc, is it a problem?
I had the same problem, even though I had the classpath in the java command. It turns out the order of the options in the java command is important, unlike the javac command which can have any order.

---

### Post by ofnuts on 2011-12-31
> **guest_user said:**
> ok I added an extra :. for the -cp option and it worked but I have another problem, 

Ini.java:9: package com.test.utils does not exist
import com.test.utils.*;

What is the cause of this issue?
My .java file isn't in a hierarchy of folders like /com/test/utils/ etc, is it a problem?
Yes... if you have a class com.test.util.Foo, it should be in some com/test/util/Too.class, where theparent of "com" is either a directory in the class path or a .jar in the class path.

---

