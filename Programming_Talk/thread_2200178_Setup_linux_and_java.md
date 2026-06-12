---
title: "Setup linux and java"
date: 2014-01-17
forum: Programming Talk
---

### Post by raac on 2014-01-17
I have a simple project in eclipse, and it is structure as follows



ApplicationTest
          |
bin         src
              |
            mainPkg
                |
              sampleTest.java


In the ApplicationTest directory I did the following command
javac -d bin -sourcepath src src/mainPkg/sampleTest.java

And it compiles

Then I execute
java /bin/mainPkg/sampleTest


And I get this...


Exception in thread "main" java.lang.NoClassDefFoundError: bin/mainPkg/sampleTest (wrong name: mainPkg/sampleTest)
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:800)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:449)
    at java.net.URLClassLoader.access$100(URLClassLoader.java:71)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:361)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:425)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:308)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:358)
    at sun.launcher.LauncherHelper.checkAndLoadMain(LauncherHelper.java:482)


Then I specified the -cp flag, but I'm not sure which folder from the jdk directory the class path should point to.

I did this...

java -cp /home/user/My-Files/libraries/jdk1.7.0_45/bin/ bin/mainPkg/sampleTest

Then I get this

Error: Could not find or load main class bin.mainPkg.sampleTest

It's a different error, does that mean that I specified the classpath correctly??

Thanks a lot for your help.

---

### Post by ofnuts on 2014-01-18
If your class is "sampleTest" in a "mainPkg" package (which means sampleTest.java contains "package mainPkg;") after the compile you should end up with a file bin/mainPkg/sampleTest.class.

And to invoke it from the command line, the classpath should point to the "bin" directory and you designate the class as mainPkg.sampleTest, ie:

```

java -cp bin mainPkg.sampleTest

```

In other words:
[LIST]
[*]the class path items are the directories (or jar) just above the "root" packages
[*]class are designated by their full path, replacing directory separators by dots
[*]the package in the class should match its position
[/LIST]

For instance if you have the following directory/file structure: a/b/c/d/e/Foo.class
[LIST]
[*]if Foo has no package then the classpath should include the directory a/b/c/d/e and the class is just "Foo"
[*]if Foo is declared in package "d.e" then the classpath should include the directory a/b/c and the class is d.e.Foo
[/LIST]

---

