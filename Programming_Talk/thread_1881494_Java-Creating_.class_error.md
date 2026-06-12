---
title: "Java-Creating .class error"
date: 2011-11-15
forum: Programming Talk
---

### Post by AlGorism on 2011-11-15
Hi people. 
I'm preparing a project. I have 20 classes. I have Main class in default package, I created another package. I imported all of the package to Main class. I compiled and run the program in Windows, there is no mistake. I'm using Reflection, which means the types of some objects are determined at runtime.
Because I create objects by reflection, I don't use **new** command for some of my classes. I mean I don't code something like this for some of my classes:
```
new A();
new B();
new C();
new D();
```
My problem is, I compiled the program in linux by javac command. But, for the classes I create via reflection, there is no .class file after compilation. Assume that I create objects for A, B, C, and D classes via reflection. Compiler doesn't create A.class, B.class, C.class, and D.class files. When I try to run the program, java throws class not found exceptions for A, B, C, and D classes. So, I wrote this code segment to entrance of my Main class:
```
new A();
new B();
new C();
new D();
```
After compilation, .class files for A, B, C, and D are created. When I run the program, it finished successfully. 
My question is, wtf?!? Do I have to write some crazy staff like this to run my program?

---

### Post by dileepm on 2011-11-16
Compile using command ```
javac -d .
```

---

