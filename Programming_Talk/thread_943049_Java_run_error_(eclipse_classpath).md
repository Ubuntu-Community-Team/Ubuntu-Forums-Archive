---
title: "Java run error (eclipse classpath)"
date: 2008-10-09
forum: Programming Talk
---

### Post by Nevyn on 2008-10-09
Hello!

Today I was studying (in eclipse) for my beginners Java programming exam, when I accidentally messed up the view (closed the "run"-window). After I had restored the windows to it's original layout, I suddenly couldnt run any programs I'd previously written that used to work perfectly. I can't think of anything I've done to cause it (even though I obviously have).

No compilation error, but run error ```
Exception in thread "main" java.lang.NoClassDefFoundError: AdditionTable
```, where AdditionTable is the program I'm trying to run.

I've been googling for a few hours and seen many with the same error code and they all seem to have gotten the same diagnosis; wrong CLASSPATH. After several hours of researching I still haven't been able to find a solution that I understant enough to be able to do. The eclipse documentation also gave me nothing.

Anybody got an idea where I change this CLASSPATH, and more importantly: what should I change it to?

Using Java 1.5, I have made damn sure I have no other Java version installed.

Typing "dpkg -l | grep libswt" in the console gave me this:
```
ii  libswt3.2-gtk-gcj                          3.2.2-5ubuntu2                                       Fast and rich GUI toolkit for Java, gtk2 (GC
ii  libswt3.2-gtk-java                         3.2.2-5ubuntu2                                       Fast and rich GUI toolkit for Java, gtk2 ver
ii  libswt3.2-gtk-jni                          3.2.2-5ubuntu2                                       Platform dependent files for libswt3.2-gtk-j
```

And typing "java -version" gives me:
```
java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)
Java HotSpot(TM) Server VM (build 1.5.0_15-b04, mixed mode)

```

Would very much appreciate any help given, since the exam date is closing in fast.

---

### Post by mosty friedman on 2008-10-10
i'm not very familiar with that...did you make sure that the file name and class name are the same?

---

### Post by jespdj on 2008-10-10
The SWT stuff doesn't have anything to do with your program.

First, check if you're in the Java perspective in Eclipse: Window / Open Perspective / Java. Second, check if your source code is being compiled. Project / Build Automatically should be checked.

You can run your program by right-clicking the class in the Project Explorer (on the left), and then selecting Run As / Java Application in the popup menu.

To set more options for running your program, select Run / Run Configurations... in the main menu bar.

---

### Post by Nevyn on 2008-10-10
Thanks for trying, jespdj! 
Yes, I have the Java perspective (that was what I was trying to restore when it all got messed up in the first place).
Build automatically is checked.
I have previously been able to run programs just fine, using just the 'Run -> Run as -> Java application' method.
I can not find the 'Run -> Run configuration'. When I try to 'Run-> Run as' the menu says '(non applicable)'. 

The only "configuration" I find in the Run menu is 'Run -> External Tools -> New configuration', that when clicked generates the error "Variable References non-existing resource: ${workspace_loc:/labb4/AdditionTable.class}".
When i look in the file systems folder workspace->labb4 there is a file called AdditionTable.class, and it has no errors.

Still no look solving the problem, I have no idea where to look for answers. Appreciate any help!

---

### Post by jespdj on 2008-10-10
Hmmm.... it sounds like there's something strange going on with your project, maybe for some reason Eclipse doesn't see it as a Java project anymore.

You could try creating a new Java project in Eclipse and copying your source files into the new project.

---

### Post by Nevyn on 2008-10-12
That seems absolutely right! When creating an entire new Java-project, it works fine. Thanks for the idea!

Have you also got an idea how to make the old projects recognized as Java-projects? Not all that important since I can copy-paste, but it'd be nice to learn something from my error=)

---

### Post by achelis on 2008-10-12
There is a .project in the root folder of your project. It contains information about project-type and how the project should be build. 
```

<buildCommand>
	<name>org.eclipse.jdt.core.javabuilder</name>
	<arguments>
	</arguments>
</buildCommand>

```
should be a child of buildSpec and
```

<nature>org.eclipse.jdt.core.javanature</nature>

```
should be a child of natures. Look at a working .project file for a full example.

---

