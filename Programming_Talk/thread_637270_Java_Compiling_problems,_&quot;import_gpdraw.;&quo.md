---
title: "Java Compiling problems, &quot;import gpdraw.*;&quot;"
date: 2007-12-10
forum: Programming Talk
---

### Post by nystud162 on 2007-12-10
Okay, I have been trying to do this for awhile.  I installed java jdk from the java site (.bin file). When I try to compile a program, it works fine.  but now im trying to compile a program that imports gpdraw.jar ```
import gpdraw.*; 
```
When i compile this: ```

import gpdraw.*;

class DrawTest

{
private DrawingTool myPencil;
private SketchPad myPaper;


	public DrawTest()
	{
		myPaper = new SketchPad(300,300);
		myPencil = new DrawingTool(myPaper);
	}

	public void draw()
	{
		myPencil.forward(50);
	}




}
```

i get this is the compiler: (I have a seperate .java file for the main)```
evan@evan-compaq-ubuntu:~/Desktop/java/DrawTest$ javac DrawTest.java
DrawTest.java:2: package gpdraw.jar does not exist
import gpdraw.jar.*;
^
DrawTest.java:6: cannot find symbol
symbol  : class DrawingTool
location: class DrawTest
private DrawingTool myPencil;
        ^
DrawTest.java:7: cannot find symbol
symbol  : class SketchPad
location: class DrawTest
private SketchPad myPaper;
        ^
DrawTest.java:12: cannot find symbol
symbol  : class SketchPad
location: class DrawTest
                myPaper = new SketchPad(300,300);
                              ^
DrawTest.java:13: cannot find symbol
symbol  : class DrawingTool
location: class DrawTest
                myPencil = new DrawingTool(myPaper);
                               ^
5 errors

```

obviously its all originating from ```
import gpdraw.*;
```

I have no idea why this is doing this, i have searched google and havent found anything.  This is the first time I started programing java in linux, I normailly use JCreator in school.

---

### Post by rekahsoft on 2007-12-10
```
javac -sourcepath src -classpath path/to/gpdraw.jar
```
I would recommend taking a moment and learning ant...it makes buildes much easier...also i might add Netbeans does this for you ;) so does eliclipse but i like NetBeans a lot more

---

### Post by nystud162 on 2007-12-11
thing is, is that this happens whenever I import anything.

I went to the site and downloaded and installed Netbeans 6.0 with Java JDK, and still whenever i compile this test program, I get the same exact error.

Also, im unsure about where all of the .jar files are located, i never had to deal with locating the directory of the .jar files on my windows pc.

heres my output of: ```
sudo update-alternatives --config java

```
```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

```

does that have anything do do with whats going on? ^

---

### Post by Elegorod on 2007-12-13
gpdraw package is not included in Sun Java. It's not a problem with JDK or update-alternatives.
Do you have a file named gpdraw.jar or similar? When you open this jar file in archive manager, it should be gpdraw directory inside. If yes, copy it to the same directory as your source file. rename to gpdraw.jar and run a command:
```

javac -classpath gpdraw.jar DrawTest.java

```

---

### Post by SNYP40A1 on 2007-12-13
> **rekahsoft said:**
> ```
javac -sourcepath src -classpath path/to/gpdraw.jar
```
I would recommend taking a moment and learning ant...it makes buildes much easier...also i might add Netbeans does this for you ;) so does eliclipse but i like NetBeans a lot more

I really like Eclipse.  If you are programming in Java, you should be using either Netbeans or Eclipse.  Cannot live without continuous compile.

---

### Post by sh!ft on 2007-12-13
May I suggest ANT building? Great for Java since ANT isn't a system dependent shell based batch... Heh Apache Foundation!

---

### Post by nystud162 on 2007-12-14
> **Elegorod said:**
> gpdraw package is not included in Sun Java. It's not a problem with JDK or update-alternatives.
Do you have a file named gpdraw.jar or similar? When you open this jar file in archive manager, it should be gpdraw directory inside. If yes, copy it to the same directory as your source file. rename to gpdraw.jar and run a command:
```

javac -classpath gpdraw.jar DrawTest.java

```

Okay, so I'm slowly getting there, at least I think I am.  So far I've taken my single file gpdraw.jar and extracted it into my project folder and renamed the FOLDER? to gpdraw.jar. It was unclear to me where to put it.

My current file/folder architecture looks like this: 

DrawTest(folder)
        |
DrawTest.java(file)
DrawTestDriver.java(file)

gpdraw.jar(folder)
        |
*All the .class files including SketchPad.class, DrawingTool.class.... etc..*

----------

^ gpdraw.jar(folder) is in the DrawTest(folder) along with my project files (DrawTest.java and DrawTestDriver.java)


I get this when trying to compile:

```
evan@evan-compaq-ubuntu:~/Desktop/Stuff/java/DrawTest$ javac -classpath gpdraw.jar DrawTest.java
DrawTest.java:2: package gpdraw does not exist
import gpdraw.*;
^
DrawTest.java:7: cannot access DrawingTool
bad class file: gpdraw.jar/DrawingTool.class
class file contains wrong class: gpdraw.DrawingTool
Please remove or make sure it appears in the correct subdirectory of the classpath.
private DrawingTool myPencil;
        ^
2 errors

```

---

### Post by jespdj on 2007-12-16
What you put in the **import** statement in your source code should **not** be the name of the JAR file, but the name of a package in the JAR file.

I don't know what "gpdraw" is, so I can't tell you what the right package name is. Do you have API documentation for gpdraw? There you should be able to find what package(s) are available in its API.

You could also have a look what's inside the JAR file, try this:
```
jar tvf gpdraw.jar
```
to list the contents of gpdraw.jar.

The last error message in your post suggests that the classes in gpdraw.jar are not packaged correctly. Maybe you should contact the person who made gpdraw.jar and tell them this.

---

