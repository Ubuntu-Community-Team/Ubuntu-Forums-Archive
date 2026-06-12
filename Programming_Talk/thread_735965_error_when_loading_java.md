---
title: "error when loading java"
date: 2008-03-26
forum: Programming Talk
---

### Post by tkmud on 2008-03-26
I am new in to java programming and i have installed java 6.0 online. my problem is that, when i create my source code and compile in dos, it give me the following error. "Exception in thread "main" java.lang.NoClassDefoundError:". i reinstalled java but stil it gives me the same problem. Now i can not do anything since it is failing to show me anything. pliz help.

---

### Post by luisromangz on 2008-03-26
What command are you using to compile in the comand line (not DOS...)?

---

### Post by themusicwave on 2008-03-26
This could be in error in the way you are compiling or in your code.

Please post both here so we can see whats going on.

---

### Post by nitro_n2o on 2008-03-26
When you run java you don't supply a filename extension 
if your class is HelloWorld.java 
then you compile with javac HelloWorld.java but to run you just say java HelloWorld without any extension 

The second issue, make sure you have a main method

---

### Post by jespdj on 2008-03-26
This is a frequent problem that Java beginners have. There's nothing wrong with your JDK installation, so re-installing Java doesn't help.

You need to make sure that you are executing the commands properly in the right directory, and you might need to set your classpath.
```

# To compile your Java source code
javac MyProgram.java

# To run your compiled Java program
java MyProgram

```
Note: When running a Java program, do not add ".java" or ".class" behind the class name - it should be just the class name.

See this: [Sun Java Tutorials - Getting Started](http://java.sun.com/docs/books/tutorial/getStarted/index.html)

---

