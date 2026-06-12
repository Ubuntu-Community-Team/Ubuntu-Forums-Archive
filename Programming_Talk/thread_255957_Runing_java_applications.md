---
title: "Runing java applications"
date: 2006-09-12
forum: Programming Talk
---

### Post by hoagie on 2006-09-12
I just started java and I made a simple project (the famous Hello World) using eclipse. I wrote the source code and then using eclipse I edited the properties of the project and made it executable. When I try to run it (run in terminal) nothing works. Any ideas?](*,)

---

### Post by yaaarrrgg on 2006-09-12
what is the error message?

if your file is named "HelloWorld.java," compiling it will produce a file named "HelloWorld.class"

you'd run the class like this:

```

java HelloWorld

```

---

### Post by hoagie on 2006-09-12
I have 2 files.HellWorld.java and HelloWorld.class. I tried the code java HelloWorld but I get an error message:
$ Exception in thread "main" java.lang.NoClassDefFoundError: Helloworld
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: Helloworld not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
](*,)

---

### Post by kaamos on 2006-09-12
> $ Exception in thread "main" java.lang.NoClassDefFoundError: Helloworld

You have the wrong case. Try Hello**W**orld instead of Hello**w**orld.

---

### Post by hoagie on 2006-09-12
$ java HelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: HelloWorld not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
:-\" :roll: ](*,)

I'm desperate, com'n theres got to be a way to solve it. 
By the way when I try to run the HelloWorld in a terminal a terminal flash opens and closes immediately.

---

### Post by kaamos on 2006-09-12
Try compiling it again in the terminal

javac HelloWorld.java
java HelloWorld

---

### Post by hoagie on 2006-09-12
Yay it worked, although this only works when I use that command. Is there a way to to that when I double click the file?

---

### Post by NewbieLearnLinux on 2006-09-12
The Ubuntu does not include develope-tools for programmers. You may need to install some libs and/or compilers to do the job...

---

### Post by hoagie on 2006-09-12
ok anyway thanks for helping me out:D

---

