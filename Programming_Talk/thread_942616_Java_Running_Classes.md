---
title: "Java Running Classes"
date: 2008-10-09
forum: Programming Talk
---

### Post by DBQ on 2008-10-09
In java suppose I have a class c1 in a package p1.  Hence this will be represented as file c1.class in director p1. 

Is there any way to run this class from ANY path? ie. not just java p1/c1?

Suppose I want to run the class as follows java /home/me/dir1/dir2/p1/c1.  The reason I want to do this is so that the process treat /home as its working directory. Is there any way to do this?  Please forgive if this is a simple question.

Thank You

---

### Post by Zugzwang on 2008-10-09
Sure. You can either package your Java program in a .jar file which you can execute from anywhere *or* tell the "java" command where to look for classes:

```
java -cp /home/me/dir1/dir2/ p1.c1
```

---

### Post by drubin on 2008-10-09
[http://en.wikipedia.org/wiki/JAR_(file_format](http://en.wikipedia.org/wiki/JAR_(file_format))

[http://java.sun.com/docs/books/tutorial/deployment/jar/](http://java.sun.com/docs/books/tutorial/deployment/jar/)

---

