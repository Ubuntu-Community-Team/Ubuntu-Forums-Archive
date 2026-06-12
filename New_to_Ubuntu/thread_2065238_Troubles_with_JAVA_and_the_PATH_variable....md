---
title: "Troubles with JAVA and the PATH variable..."
date: 2012-10-01
forum: New to Ubuntu
---

### Post by robscubelek on 2012-10-01
Hey guys. I've been using Java 7, and I cannot figure out how to change the path variable.  I have tried setting it to /home/java/bin, where javac and java and the other executables reside, but the terminal tells me that no such directory exists.

I can navigate to the programs manually, to compile and such, by going to the folder I keep my java programs in and doing something like 

rob@ubuntu:`/Documents/java$ ../../java/bin/javac HelloWorld.java

but I have been unable to set the PATH variable.

Well, thats not true, because when I echo the PATH, it has the folders that I added, but the computer doesn't recognize the folder paths.  What am I doing wrong?

I've no doubt that its just a minor misunderstanding of Linux's file hierarchy, but I can't figure it out for the life of me.

So how would I do it?

It is definitely not:
/Home/java/bin
/home/java/bin
/home/rob/java/bin

Any thoughts or input would be appreciated.

---

### Post by robscubelek on 2012-10-01
Okay so scratch that part about the PATH variable being set, I just echo'd it and none of my changes to the PATH variable were saved.  But I still have all the same problems, only now I also need to know how to permanently set the PATH variable as well.  Thanks in advance, Ubuntugurus

---

