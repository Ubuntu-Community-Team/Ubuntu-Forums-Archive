---
title: "Javac - Not working properly?"
date: 2009-01-29
forum: Programming Talk
---

### Post by Sugz on 2009-01-29
Ok, so my recent project is taking shape, however, whenever i use the terminal command JavaC
on my main class, i get a whole string of errors all of them about not being able to find symbols
Like The objects that use in the main class.
This is quite odd as When i run it in netbeans, it runs fine, with no problems at all?
Can JAVAC even handle object orientation? (Sorry that sounds thick but it seems that fundamental)

---

### Post by bruce89 on 2009-01-29
What does ```
java -version
``` say?

---

### Post by myrtle1908 on 2009-01-29
Almost certainly a problem with your build/class path.  Have a look at the build path you are using in NetBeans then use the same one when you compile on the command line.

---

### Post by HotCupOfJava on 2009-01-30
I hope I'm not insulting your intelligence, you've probably already thought of this, but there are 2 things that you may wish to check:

NetBeans uses fully-qualified names for any GUI controls from the pallete. There are no import statements (unless YOU supplied some). If the code is EXACTLY the same, this should not be a problem in the terminal...

NetBeans automatically packages classes, so the same code compiled in the terminal must be compiled from the root of the package directory, with the path spelled out in the command. If you happen to be compiling the code on a different machine (from the one you have NetBeans on), the package statement in the code may be the cause of your woes. The class would have to be placed in the exact named directory structure as the one NetBeans is using. Dependencies from other classes you created in Netbeans could also be the problem for the same reason. You may have to repackage some classes for terminal compilation.

These may not be your problem at all. I just recall running into these issues when I first started learning Java (you may be well past that and again, I'm not trying to insult your intelligence).

---

### Post by Sugz on 2009-01-30
^ is fine, any suggestions are of great help
output of Java version

java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) Server VM (build 1.5.0_13-b05, mixed mode)

And Im not using any GUI's in the final version, i will do, but at the moment its pure command line.

And finally.. i am running Javac from the src Directory that Netbeans prduces for each project. home/XYZ/mydocs/project/src/projectfiles/ ...

Erm, thats about all i can find

---

### Post by myrtle1908 on 2009-01-30
Are you using any JAR files or other compiled 3rd party classes in your project?  Regardless of where you are running javac from, you need to ensure you include these in your classpath when compiling with javac.  For example:-

```
javac -classpath .:/path/to/somejar.jar:/path/to/someclass.class MyClass.java
```

You could also setup the CLASSPATH environment variable so as to avoid having to type '-classpath ...' when compiling.

---

### Post by Zugzwang on 2009-01-30
Make sure to compile from the "package root"! For example, if your class Foo lies in package com.Bar, then switch to the directory containing the com/Bar directory and type:

```

javac com/Bar/Foo.java

```

Same about running your project. Always run it from the "package root".

---

### Post by Sugz on 2009-01-30
Tried the above.. nothing
I am not using any 3rd party Packages or .jar files
I have implemented a GUI and i have the feeling this is only going to get worse :(

---

### Post by Zugzwang on 2009-01-31
> **Sugz said:**
> Tried the above.. nothing
I am not using any 3rd party Packages or .jar files
I have implemented a GUI and i have the feeling this is only going to get worse :(

So give us the precise error message you are getting when running/compiling the program.

---

