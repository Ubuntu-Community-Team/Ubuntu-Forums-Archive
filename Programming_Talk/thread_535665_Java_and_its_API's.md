---
title: "Java and its API's"
date: 2007-08-26
forum: Programming Talk
---

### Post by JamesA on 2007-08-26
Hey guys, quick question.


I downloaded the JSR82 API to get cracking on java and bluetooth programs. It has given me two folders: bluetooth  and obex.

Both of these folders are subfolders of a directory called 'javax'. Where do i put these folders in my file system?

What i mean is, what directory should these folders be in for java to reconize the api as installed?

---

### Post by samjh on 2007-08-26
You need to compile the sources.

Then you either use the class files directly, or to make it easier in the long-term, pack the class files into a .jar file (keep the javax/bluetooth and javax/obex directory structure).

Refer to the documentation on Sun's website for how to create a jar file:
[http://java.sun.com/docs/books/tutorial/deployment/jar/build.html](http://java.sun.com/docs/books/tutorial/deployment/jar/build.html)

To compile programs that use the JSR82 classes, you will need to specify -classpath to the directory containing your JSR82 classes when you use javac.
For example, if my JSF82 classes are in /home/me/bluetooth.jar, then I will use: javac -cp /home/me/bluethooth.jar MyProgram.java
Likewise for running your programs.

---

