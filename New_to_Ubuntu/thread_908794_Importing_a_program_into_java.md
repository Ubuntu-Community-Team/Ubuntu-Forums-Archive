---
title: "Importing a program into java"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by CorwinShiu on 2008-09-02
For my computer science class, I have to put gpdraw.jar into my java. They only gave the instructions for Windows so I don't really know what to do. Here are the instructions:

> Installing gpdraw:

We will use the ICT gpdraw.jar libraries in a lot of our lessons. Here is quick way to ensure it is on your classpath so you will have access to it wheAn we program.

1) Download gpdraw.jar file from our website and put it in these two folders on your machine:
	- C:\Program Files\Java\jdk1.6.0_02\jre\lib\ext
	- C:\Program Files\Java\jre1.6.0_02\lib\ext
	(Note: Your path to the ext directory may be different.)
2) At the top of your java file type : import gpdraw.*;
3) If the program does not compile*, then you need to follow these instructions:
	a) Right-click on the project name --> Properties
	b) Select Java Build Path on Left Menu
c) Click  Libraries Tab
d) Add External Jars
	e) C:\Program Files\Java\jre1.6.0_02\lib\ext\gpdraw.jar
	f) Click OK.

It should compile* now.



*  Remember that in Eclipse we have incremental compiling. Eclipse, in very regular and quick intervals, calls javac to see if the file we are creating will compile. You will know if gpdraw.jar file is on your classpath if the following line in your java file is not underlined in red(yellow is OK):
	import gpdraw.*; 

	If it is not underlined in red, eclipse is telling you that it see the gpdraw library in your classpath and can compile. If it is in underlined red you need to add the library to your classpath.


Can anyone explain where to put my file? Thanks.

---

### Post by CorwinShiu on 2008-09-02
Okay so I think I found one:

/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext

not sure if there is another.

Also I can't drag the file in. I  don't have root positions. I tried logging onto root but it says I couldn't log on. Can someone explain how to drag the file in?

---

### Post by lsmobrian on 2008-09-02
If you're using eclipse, I wouldn't even worry about putting the jar file in the jdk directory.  when you create a new project, copy and paste the jar file into the directory(refresh using F5 if it doesnt show up)  right click the jar file and choose  build path -> add to build path.   your jar will be on your class path and you can use it now.


if you are using it a lot and dont want to bother with it every time you can add a user library that will add it to your classpath everytime in eclipse

goto preferences and find the java tab. there should be a user libraries subgroup.  create a new library and then choose add jars.  find the jar file you want to add, now anytime you create a project this jar is on the classpath.


dont recommend adding it to the actual jdk/jre directory, but thats just me




as far as the root thing goes, ubuntu doesn't have a root user by default that can be used to login, the normal action would be to 'sudo <command needing root privilege>' or 'sudo su' then the command.   be careful what you do though, you can break things if youre not sure what youre doing

---

### Post by CorwinShiu on 2008-09-02
Thanks, it works. I don't mind having to copy it so it's okay ;P.

---

