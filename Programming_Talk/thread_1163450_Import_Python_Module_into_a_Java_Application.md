---
title: "Import Python Module into a Java Application"
date: 2009-05-18
forum: Programming Talk
---

### Post by Pyro.699 on 2009-05-18
Hello,

I was wondering if it is possible to import a PYC (Python Module File) into a java application, and if so... how?

Thanks
~Cody Woolaver

---

### Post by simeon87 on 2009-05-18
You could try Jython: [http://www.jython.org](http://www.jython.org).

---

### Post by Pyro.699 on 2009-05-18
I've heard about jython although if it is possible id like to keep the 2 languages separate.

Thanks
~Cody Woolaver

---

### Post by Reiger on 2009-05-19
Jython is not just a way to "whack some Python-like-stuff on top of Java" or "inline Java with Python" or things like that. You can access Python code as if it were Java and vice versa with it.

---

### Post by CptPicard on 2009-05-19
... although jJthon is its own implementation, written in Java. You can't grab a .pyc file (as far as I know) and access it from Jython, and neither can you do so from Java.

---

