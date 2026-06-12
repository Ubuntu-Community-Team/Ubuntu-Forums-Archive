---
title: "How do I edit a java source code file, and then run it?"
date: 2007-01-02
forum: Programming Talk
---

### Post by user1397 on 2007-01-02
I found this java game online: [http://www.addictinggames.com/soccerslime.html](http://www.addictinggames.com/soccerslime.html) which has a downloadable version with source code.  The source code is made up of 3 files: 
WorldCupSoccerSlime.java
WorldCupSoccerSlime.class
WorldCupSoccerSlime.html
I downloaded it, and I tried to edit the .java file (I changed some of the world cup international team names to their correct spelling, i.e. instead of Seth Efrica I put 'South Africa' and so forth) with the netbeans IDE in windows (yes I installed everything correctly, including the java 6 dev kit and the runtime env

I don't know how to proceed though, the farthest I've gotten with java before this was successfully compiling the HelloWorld app

worth to note: I tried recompiling it after editing the team names, but it gave me this error:

> 
init:
deps-jar:
Created dir: C:\Documents and Settings\Owner\WorldCupSoccerSlime\build\classes
Compiling 1 source file to C:\Documents and Settings\Owner\WorldCupSoccerSlime\build\classes
C:\Documents and Settings\Owner\WorldCupSoccerSlime\src\worldcupsoccerslime\Main.java:21: class WorldCupSoccerSlime is public, should be declared in a file named WorldCupSoccerSlime.java
public class WorldCupSoccerSlime extends Applet
Note: C:\Documents and Settings\Owner\WorldCupSoccerSlime\src\worldcupsoccerslime\Main.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
1 error

---

### Post by jblebrun on 2007-01-02
The error message is telling you exactly what you need to know. For some reason, you seem to have renamed WorldCupSoccerSlime.java to Main.java. But, as the error message states, since the file contains a public class called WorldCupSoccerSlime, the file must be called WorldCupSoccerSlime.java. 

To run to the compiled applet, just put the html and the class file in the same directly, and open the html file in any browser with Java support.

---

### Post by user1397 on 2007-01-02
> **jblebrun said:**
> The error message is telling you exactly what you need to know. For some reason, you seem to have renamed WorldCupSoccerSlime.java to Main.java. But, as the error message states, since the file contains a public class called WorldCupSoccerSlime, the file must be called WorldCupSoccerSlime.java. 

To run to the compiled applet, just put the html and the class file in the same directly, and open the html file in any browser with Java support.ah ok I got it.  when creating a new project, I was supposed to call the main class file 'worldcupsoccerslime.WorldCupSoccerSlime' and then it compiled successfully.  Tried it in firefox, and the team names were changed to what I put.  Awesome.

---

### Post by jblebrun on 2007-01-02
> **erik1397 said:**
> ah ok I got it.  when creating a new project, I was supposed to call the main class fil 'worldcupsoccerslime.WorldCupSoccerSlime' and then it compiled successfully.  Tried it in firefox, and the team names were changed to what I put.  Awesome.

Ah, so you used a GUI that create project files for you! Well, sounds like you got it working, so congrats!

By the way, you could do this very easily from the command line without using a GUI:

1. Edit the java file as you want
2. just type "javac WorldCupSoccerSlime.java"
3. That's all!

---

