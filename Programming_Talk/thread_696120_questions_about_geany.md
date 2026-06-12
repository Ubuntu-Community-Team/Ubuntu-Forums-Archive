---
title: "questions about geany"
date: 2008-02-13
forum: Programming Talk
---

### Post by Hranj on 2008-02-13
im taking a computer science class in school right now, learning java, and im wanting to work on some of the programs at home. so i installed geany and i wrote some code but im having trouble compiling and running it.

when i hit compile i get the error message

> /bin/sh: javac: not found

im guessing this is where its actually looking for java, how can i change this and does anyone know where i should change it to?

---

### Post by Wugglz on 2008-02-13
It seems like you haven't installed the jdk. Try running:

> sudo aptitude install sun-java6-jdk

---

### Post by Hranj on 2008-02-13
ok, i installed the jdk and im now able to compile. but i tried running a program now and it gives me this error message and i have no idea what to make of it.

> Exception in thread "main" java.lang.unsupportedclassversionerror: bad version number in .class file

and then it has a bunch of at and then the locations of the errors that i dont want to type out unless its necesary.

---

### Post by Hranj on 2008-02-21
bump.

any advice???

---

### Post by Zugzwang on 2008-02-23
Did you try
```

sudo update-alternatives --config java

```
and selected the Sun JVM?

---

