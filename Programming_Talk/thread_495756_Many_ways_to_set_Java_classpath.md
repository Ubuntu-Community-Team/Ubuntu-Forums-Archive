---
title: "Many ways to set Java classpath?"
date: 2007-07-08
forum: Programming Talk
---

### Post by QwUo173Hy on 2007-07-08
I've downloaded Java 6.1 to test an application for someone. I can use
```
sudo update-alternatives --config java
```
To change between installed versions of java, but I've just extracted this zip on the desktop and don't want to install it.

I've managed to get $JAVA_HOME to point to the correct folder but $JAVA is blank. I did this in /etc/environment

When I run "which java" I get
```
/usr/bin/java
```
ls -lh for this gives
```
lrwxrwxrwx 1 root root 22 2007-05-27 05:20 /usr/bin/java -> /etc/alternatives/java
```
and ls -lh /etc/alternatives/java gives
```
lrwxrwxrwx 1 root root 40 2007-07-07 17:09 /etc/alternatives/java -> /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
```

I'm totally confused. This program uses a binary executable so I cant run it with the java command directly. I don't want this new java intergrated to the system at all, it's just for testing. How can I do this?

Thanks,
Jarlath

---

### Post by nitro_n2o on 2007-07-08
you don't need to change the classpath.. 
did you try to go in the new java folder and type  ```
java myclass 
``` this should work!! you just want to run java, you don't even need the jdk it's enough to have the jre

if you want to run a jar just do this: java -jar my_classes.jar

Hope that helps

---

### Post by QwUo173Hy on 2007-07-08
Hi nitro-n2o. I am aware of this. But the file is not a jar, it is a binary executable which uses java so I cannot do this.

---

### Post by nitro_n2o on 2007-07-08
ohh... so it's not only a .class file... I don't know then.. sorry for the misunderstanding, i think you'll need to change your system class path... 

but also you can try this: java -classpath /path/to/new/java your_program 
It might work, i really don't know never tried it for this purpose

---

### Post by nitro_n2o on 2007-07-08
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) check out this.. scroll down a little bit for "selecting the default java jdk" you should edit /etc/jvm also

good luck

---

### Post by Ramses de Norre on 2007-07-08
You're not forced to use the alternatives system, relink /usr/bin/java and the alternatives don't influence java anymore...
You can also put the directory including your java executable (so the java vm, not your binary program) in your path before the one containing the alternatives-configured java (export PATH=/your_folder:$PATH).

BTW: it's confusing to talk about the classpath, the classpath is the collection of directories where java searches for classes, as I understand you correctly you're talking about the path used by the OS to retrieve binaries which is mostly referred to as just "path".

---

