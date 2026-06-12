---
title: "[SOLVED] Java/C library for code analysis"
date: 2008-03-25
forum: Programming Talk
---

### Post by fyplinux on 2008-03-25
I am seeking for a library either in C or Java that could scan over a source code file, output all the global variables and the function prototypes.

Although it is not hard to do it personally, using the library is more easier.

---

### Post by meatpan on 2008-03-25
The doxygen system provides a nice summary of functions and globals (among other things).  Be aware that the doxygen library requires a bit learning, and might be a more sophisticated solution than necessary for your situation.

[http://www.stack.nl/~dimitri/doxygen/](http://www.stack.nl/~dimitri/doxygen/)

---

### Post by themusicwave on 2008-03-25
If the Code is written in Java, then have a look at the Java Reflections.

They can read compiled Java byte code and output all kinds of information about the code.

[http://java.sun.com/javase/6/docs/api/java/lang/reflect/package-frame.html]("http://java.sun.com/javase/6/docs/api/java/lang/reflect/package-frame.html")

---

### Post by drubin on 2008-03-25
If the code is java, you could just generate "JavaDocs" ?

---

