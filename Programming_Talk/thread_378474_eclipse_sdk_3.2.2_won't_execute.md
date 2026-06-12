---
title: "eclipse sdk 3.2.2 won't execute"
date: 2007-03-07
forum: Programming Talk
---

### Post by mj3 on 2007-03-07
I'm new to Ubuntu and I've been saddled with a project to build a development environment using IBM's tutorials from developworks. I've just downloaded the lastest version of eclipse and I've already extracted the files, but when I made my eclipse shortcut to the desktop and tried to execute eclipse I got this funky error message: 
VM terminated. Exit code=1
/usr/bin/java
-jar startup.jar
-os linux
-ws gtk
-arch x86
-launcher /home/localtest/Desktop/eclipse
-name Eclipse
-showsplash 600
-exitdata 10f000d
-vm /usr/bin/java
-vmargs
-jar startup.jar 

Can anyone tell me what that error refers to and how can it be fixed or find a way around it?  Thanks a bunch!

---

### Post by mj3 on 2007-03-07
ok I found out what the problem was, turns out I didn't have the right version of java installed. causing it to not function properly with eclipse 3.2.2! taken care of now!:)

---

