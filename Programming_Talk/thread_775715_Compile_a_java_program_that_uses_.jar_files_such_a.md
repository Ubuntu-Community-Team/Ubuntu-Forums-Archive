---
title: "Compile a java program that uses .jar files such as iText"
date: 2008-04-30
forum: Programming Talk
---

### Post by mattgaunt on 2008-04-30
Hey guys

I've written a program in java that uses the iText api which is a .jar file. Now I've programmed it using netbeans but want to ensure it can be compiled outside of netbeans.

Does anyone know how I can achieve this??

Thanks alot

Gaunt

---

### Post by Zugzwang on 2008-04-30
You can compile it adding the iText jar file to the classpath, for example:

```

javac -cp /path/to/the/iText.jar yourpackage/Yourclass.java

```

---

### Post by Tomosaur on 2008-04-30
> **mattgaunt said:**
> Hey guys

I've written a program in java that uses the iText api which is a .jar file. Now I've programmed it using netbeans but want to ensure it can be compiled outside of netbeans.

Does anyone know how I can achieve this??

Thanks alot

Gaunt

If the iText .jar file has a liberal licence, you should be able to just redistribute it.

In terms of distributing an actual build of your software (which is what I think you may really mean, as people wishing to compile your software can just get the iText.jar file themselves), you can create a subdirectory of the dist/ directory in your netbeans project folder, called 'lib', then put the necessary libraries and stuff in that directory.

---

### Post by mattgaunt on 2008-04-30
cheers for the help, i got netbeans to accept the library but i was hoping to do it via command line (Not the biggest fan of netbeans) think the classpath will do it.

Thanks for the help guys

Gaunt

---

