---
title: "Eclipse won't accept java1-6"
date: 2007-04-12
forum: Programming Talk
---

### Post by wiebers10 on 2007-04-12
I installed eclipse using synaptic in feisty.  Along with that I installed jre-1.4 and it worked fine but recently I saw that there were packages for java 6.  I installed the jre for java 1.6 and then added it to the eclipse and changed the compliance level to 6.0.  Now it won't let me create any projects either using 1.4, 1.5, or 1.6.

---

### Post by phossal on 2007-04-12
It's named Feisty for a reason. ;) How do you even *get* Feisty?

---

### Post by Nikron on 2007-04-12
Wait, how did you change the compliance?  I changed it by right clicking the JRE in my project and changing the path to the 1.6.

---

### Post by phossal on 2007-04-12
You can set the compiler compliance level via the toolbar:
Window -> Preferences -> Java -> Compiler -> Compiler compliance level

If JDK 6.0 wasn't installed correctly, which often happens using the packages - and more often on Feisty - you can't create a new project. 

The simplest, most straightforward way to avoid these kinds of problems is to get the JDK and eclipse directly from their respective sites. Get the 32-bit versions. Both Java and eclipse can be run without integrating them into your system - so long as you define JAVA_HOME in your .bashrc.

---

### Post by wiebers10 on 2007-04-12
Thanks a lot I will try that and get back to you.

---

