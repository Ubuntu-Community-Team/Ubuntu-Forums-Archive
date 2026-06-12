---
title: "Eclipse crash in 8.04"
date: 2008-04-27
forum: Programming Talk
---

### Post by achelis on 2008-04-27
Hi.
I just upgraded to Hardy Heron, and now Eclipse decided to make frequent crashes. I've tried both with Eclipse 3.2 from the repos and Eclipse 3.4M5 from eclipse.org. Only the 3.4M5 from eclipse.org worked without problems before.

Has anyone else experienced similar issues?

I'm using the args:  -vmargs -XX:MaxPermSize=512m 
which was needed before to avoid crashes.

```

JVM terminated. Exit code=1
/usr/bin/java
-XX:MaxPermSize=768m
-jar /home/kavi/Programs/eclipse_3.4M5/plugins/org.eclipse.equinox.launcher_1.0.100.v20080205.jar
-os linux
-ws gtk
-arch x86_64
-showsplash
-launcher /home/kavi/Programs/eclipse_3.4M5/eclipse
-name Eclipse
--launcher.library /home/kavi/Programs/eclipse_3.4M5/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.100.v20080201/eclipse_1108.so
-startup /home/kavi/Programs/eclipse_3.4M5/plugins/org.eclipse.equinox.launcher_1.0.100.v20080205.jar
-exitdata 3468025
-vm /usr/bin/java
-vmargs
-XX:MaxPermSize=768m
-jar /home/kavi/Programs/eclipse_3.4M5/plugins/org.eclipse.equinox.launcher_1.0.100.v20080205.jar 
```

So far the problem seems to be connected to:
1) Making a new project
2) Changing the build path of a project (ie. adding a jar-file)

I'm still new in the Linux world, but am trying to get around :)

---

### Post by gekkio on 2008-04-28
You seem to be running 64-bit hardy, is that correct?

Unfortunately there's a bug in Sun JVM which causes these crashes. Here's the relevant bug in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/174759]("https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/174759")

Try downgrading to Java 6 Update 3 (use the packages from Gutsy Gibbon). It's the only working Sun Java 6 version I know of. Even the openjdk-packages crash on Hardy 64-bit. You could also try an alternative JDK, such as IBM JDK or JRockit.
Please note that this is a JVM bug, not directly related to Hardy. So don't hate Hardy, hate the JVM. :)

Let me know if you need instructions to any of the solutions above.

---

### Post by achelis on 2008-04-28
Yes I'm running 64-bit (beginning to think it's more trouble than it's worth really..)

Ah it's good to know it's not the fault of Hardy :)

I'm not sure how I should downgrade, so if you don't mind I'd like to know :) 

Thanks.

EDIT: Just trying this and looking to be alright - I'll to play around a bit more to see if it's really fixed the problems.

> 
Eclipse doesn't crash anymore but it is slower.
I add -Xint in my eclipse.ini, the jvm don't try to optimize by compiling native code (mixed mode).
I havn't test all jvm/eclipse with this option, but you can try.
(Eclipse really eat more CPU with -Xint ! :( so it isn't a good solution)


And thanks for the link!

---

### Post by olaf-g on 2008-05-22
I ran into the same, but in the thread at launchpad mentioned above is a better workaround now. Just add this line to your eclipse.ini:

```
-XX:CompileCommand=exclude,org/eclipse/core/internal/dtree/DataTreeNode,forwardDeltaWith

```

The old workaround disabled the jit completely, the newer one just excludes a certain instruction from the jit. Works fine for me with hardy final 64 bit, sun-java-6 64 bit on a core2duo machine.

---

### Post by mbeltagy on 2008-05-23
Thanks olaf-g. That worked for me.

---

### Post by mbeltagy on 2008-05-27
Even with olaf-g's fix, I found that eclipse sometimes crashes while I am debugging. 

I switched to  IBM's Java 1.6 64 bit JVM, and Eclipse has been stable since.

---

### Post by olaf-g on 2008-05-29
Jeez... today I had another crash. Now I had to add another instruction to the exclude list:
```

-XX:CompileCommand=exclude,org/eclipse/core/internal/dtree/DataTreeNode,forwardDeltaWith
-XX:CompileCommand=exclude,org/eclipse/jdt/internal/compiler/lookup/ParameterizedMethodBinding,<init>
```

So my method is to run eclipse from the commandline. When the crash occurs the jvm dumps a hs_err_pidXX.log file to the current directory. Examine it and locate the line 'Current CompileTask:' and you see which instruction caused the crash. add it to the exclude list.

Well that's very ugly but I can work. If this goes on I'll switch to IBM's jdk, too. At least there is already a bug filed at sun:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6614100](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6614100)

Cheers

Olaf

---

### Post by mmore on 2009-04-07
hi , 

i am also new in linux, i have the same problem of eclipse crash,

but i am using eclipse to run python code. 

i don't know if  JVM might has anything with this.

i started the eclipse from command , and i noticed that message appeared while lunching
"
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found
*sys-package-mgr*: can't create package cache dir, '/usr/lib/eclipse/plugins/org.python.pydev.jython_1.2.5/cachedir/packages'

"

i got into eclipse to unmark this plugin, but the problem still exist , 

any suggestions ???

---

### Post by jespdj on 2009-04-07
mmore, welcome to the forums.

It looks like you are using GNU Java. Install Sun Java and use that instead, because Eclipse does not work very well with GNU Java (and besides that, GNU Java is slow, incompatible and obsolete).
```
sudo apt-get install sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
```

---

### Post by mmore on 2009-04-08
> **jespdj said:**
> mmore, welcome to the forums.

It looks like you are using GNU Java. Install Sun Java and use that instead, because Eclipse does not work very well with GNU Java (and besides that, GNU Java is slow, incompatible and obsolete).
```
sudo apt-get install sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
```



unfortunately  this solution did not help, i tried it but the problem still exists.

also i have a question , is Java version has anything with this problem , as i am using eclipse only for python programs

---

### Post by jespdj on 2009-04-08
Eclipse is written in Java itself, you must have Java installed to be able to run Eclipse.
> *sys-package-mgr*: can't create package cache dir, '/usr/lib/eclipse/plugins/org.python.pydev.jython_1.2.5/cachedir/packages'
How did you install Eclipse; did you install it using the Ubuntu package management system or did you install it manually?

The error message looks like Eclipse is trying to create the directory mentioned in the error message, but it can't (most likely because the user under which you're running it does not have permissions to do this). You can try creating the directory manually:
```
sudo mkdir /usr/lib/eclipse/plugins/org.python.pydev.jython_1.2.5/cachedir/packages
sudo chmod 777 /usr/lib/eclipse/plugins/org.python.pydev.jython_1.2.5/cachedir/packages
```

---

