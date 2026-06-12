---
title: "running java program in ubuntu"
date: 2009-03-10
forum: Packaging and Compiling Programs
---

### Post by iaragorn on 2009-03-10
Hello,

I don't know if I am in the correct section of forum, but I will try it here.
I have ubuntu 8.04.
I am trying to run java program from ntfs partition (windows).
If am running it through ubuntu (java -jar program.jar) and I got following:

Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file

But version JRE and JDK where program was compiled is the same.
If I try to run it from NetBeans6.1 I got following:

Exception in thread "main" java.lang.NoClassDefFoundError: core/Main

BUT!!!
If I copy program.jar on linux partition, it is running correctly in ubuntu and in netbeans also.

How to solve this kind of problem?

Thank you.

---

### Post by ashwoods on 2010-04-20
I will answer this in case somebody is googling here, as it was just solved on irc for somebody.

if you cannot open a java, eclipse, or any other program from a ntfs partition, it is probably set on noexec.

you can check this by listing how the partions are mounted.
this can be corrected by adding a exec to the partions in /etc/fstab

```
/dev/sda2 /media/sda2  ntfs nls=iso88591,group=developer,users,exec,umask=000  0  0
```

---

