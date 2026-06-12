---
title: "Javac Issues"
date: 2014-02-10
forum: Programming Talk
---

### Post by nothankyou273 on 2014-02-10
I need to be able to compile .java files.
When I run javac hello.java the file cannot be found. I've saved the file into my home folder inside a folder called test. Do I need to create a path with javac to this folder? I will be saving all my .java/.class files there. How would I do this?

---

### Post by ofnuts on 2014-02-10
Which file is not found. hello.java? What is the current directory when you start javac?

---

### Post by nothankyou273 on 2014-02-10
hello.java is not found.

---

### Post by ofnuts on 2014-02-11
So what is your current directory when you invoke javac and what are its contents?

---

### Post by raymond10 on 2014-02-12
Make sure you navigate to the .java file when using javac in the command prompt! Use
the keyword "cd" to navigate, for example if I would have the .java file in C:\Java\helloworld.java, I would open up cmd.exe and type "cd C:\Java", then type "javac helloworld.java"

---

