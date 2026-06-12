---
title: "Exception in thread &quot;main&quot; java.lang.NoClassDefFoundError:"
date: 2009-04-18
forum: Programming Talk
---

### Post by adit on 2009-04-18
When I tried to run a class file, I got the following error
```
~$gij helloworld.class 
Exception in thread "main" java.lang.NoClassDefFoundError: helloworld.class
   at gnu.java.lang.MainThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: helloworld.class not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.java.lang.MainThread.run(libgcj.so.81)
```

---

### Post by dwhitney67 on 2009-04-18
You don't specify the .class when running a compiled Java program.

```

javac MyClass.java
java MyClass

```

Since you are using the knockoff 'gcj' (or whatever it is called), substitute the appropriate commands.

---

