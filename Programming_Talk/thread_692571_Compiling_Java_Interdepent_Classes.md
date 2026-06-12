---
title: "Compiling Java Interdepent Classes"
date: 2008-02-09
forum: Programming Talk
---

### Post by DBQ on 2008-02-09
I have two java class files class1.java and class2.java.  Now class1 uses class2 as a helper class - class1 is the main class.  Under eclipse everything works fine.

Both classes are members of the same package - at the top of both files I do package myclasses, and in class1 I do import myclasses.class2.  Here is what happens when I try compiling from the command line:

javac class2.java 

No problems.

javac class1.java

I get an error that flags everything related to using class2 as "cannot find symbol".  Once again everything works fine on eclipse, but not from command line.  Any ideas??  I am using ubuntu Gutsy.

---

### Post by ZylGadis on 2008-02-10
...
Scratch that, I am sleepy. Give full source and command line, and we'll tell you what is wrong.

---

### Post by hod139 on 2008-02-10
try compiling both at once
```

javac *.java

```

---

### Post by DBQ on 2008-02-10
I tried that.  Get the following 

warning: Note: Some input files use unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.

The class files are generated.  When I run java class1 I get this:

Exception in thread "main" java.lang.NoClassDefFoundError: ProjectDemo/class

---

### Post by Zugzwang on 2008-02-10
> **DBQ said:**
> When I run java class1 I get this:

Exception in thread "main" java.lang.NoClassDefFoundError: ProjectDemo/class

Make sure that you are in the right directory before trying to execute. 
According to your post, you have the classes:
[LIST]
[*]myclasses.class1
[*]myclasses.class2
[/LIST]
i.e. you have two classes "class1" and "class2" in the package "myclasses". Make sure that both of the java files for the classes start with the declaration "package myclasses;".

I assume that you have a directory DIR where you store your stuff. Just insert the real name whenever I write DIR.

So DIR should have a directory named "myclasses" which contains java files named "class1.java" and "class2".java. Note that normally, class names should begin with an upper case letter in Java, but that's just common practice.

Then you can compile them by switching to the directory DIR an typing "javac myclasses/class1.java" and "javac myclasses/class2.java". Afterwards you can execute the first one by typing "java myclasses/class1". 

So both of your compiling and running operations must be started from the "root" (DIR) of the project. Furthermore the package names have reflect the actual directory structure used. As you get the error:
```

Exception in thread "main" java.lang.NoClassDefFoundError: ProjectDemo/class

```
You are doing something wrong as "ProjectDemo" is not the package name (and class is not the name of the class, right?).

In case you have further problems, please post the code of the two classes here and name the directories you stored them in.

---

### Post by DBQ on 2008-02-10
Thank you, Everything worked.

---

