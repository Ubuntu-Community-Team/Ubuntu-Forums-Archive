---
title: "About Java"
date: 2010-03-17
forum: Programming Talk
---

### Post by huangyingw on 2010-03-17
Hello,
    I have a naiive question about java.
    For example, I have a file, named "/media/myproject/git/java/hello-world/helloWorld.java", and compile to generate a new "/media/myproject/git/java/hello-world/helloWorld.class" file.
    So, if I run ```
java helloWorld 
``` within the directory "/media/myproject/git/java/hello-world/", I could get what I expect.
    But, if i run ```
java /media/myproject/git/java/hello-world/helloWorld 
``` outside the directory "/media/myproject/git/java/hello-world/", I would get exception:java.lang.ClassNotFoundException.
    What's the fault and how could I call a class with full path name of a java class?

---

### Post by JoeWheeler on 2010-03-17
I'm a bit of a noob to compiling java in terminal but have you tried putting .java at the end?

---

### Post by CptPicard on 2010-03-17
This has to do with how Java organizes code into packages and how that relates to the directory structure. Briefly put, the layout of subdirectories corresponds to the package structure... class foo.bar.SomeClass is expected to reside in foo/bar/Someclass.class.

Read up on this issue and "classpath" :)

---

### Post by falconindy on 2010-03-17
The problem lies within Java and its package naming scheme. When you pass "java /media/myproject/git/java/hello-world/helloWorld", the JVM is expecting to eventually resolve a class helloWorld buried in the package media.myproject.git.java.hello-world. What you need to do is specify the class path as the path to the file so that you can specify the actual class on its own.

```
java -cp /media/myproject/git/java/hello-world helloWorld
```

edit: too slow! Damn you CptPicard.

---

### Post by huangyingw on 2010-03-18
> **JoeWheeler said:**
> I'm a bit of a noob to compiling java in terminal but have you tried putting .java at the end?
No, this would not take effect.

---

### Post by huangyingw on 2010-03-18
> **falconindy said:**
> The problem lies within Java and its package naming scheme. When you pass "java /media/myproject/git/java/hello-world/helloWorld", the JVM is expecting to eventually resolve a class helloWorld buried in the package media.myproject.git.java.hello-world. What you need to do is specify the class path as the path to the file so that you can specify the actual class on its own.

```
java -cp /media/myproject/git/java/hello-world helloWorld
```

edit: too slow! Damn you CptPicard.
Thank you and CptPicard. this works for me. It seems that my env setting in Ubuntu does not totally works.

---

