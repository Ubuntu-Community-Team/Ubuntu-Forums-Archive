---
title: "importing a library  to Netbeans ."
date: 2009-07-11
forum: Programming Talk
---

### Post by rsiddharth on 2009-07-11
I have a .zip file containing source code written in Java , The code is logically packaged and each package has its own build.xml file and the code seems to be not compiled and all source code files have .java extensions . How should I import it to Netbeans and use it ( the codes in the .zip file ) as a library ? . 

I somehow intuitively realize that the code has to be compiled before it can be used has a library and I need help in this aspect too . The build.xml presumably is used to compile the source codes in bulk  and it needs ' ant ' . 

Here is the[ link]("http://www.mindviewinc.com/TIJ4/CodeInstructions.html") where the author of the code gives instructions on how to get started , but he has given instructions for Windows users and has ignored ' how tos ' for Linux counterparts .

Thank you for your help community .

---

### Post by doas777 on 2009-07-11
I'm pretty sure that if you tell it to create a new project, netbeans will ask you if you want to create it from an existing ant bundle. if not netbeans, eclipse does it.
then compile your project, and once you have a jar, reference it from your projects.

good luck

---

### Post by rsiddharth on 2009-07-12
> **doas777 said:**
> I'm pretty sure that if you tell it to create a new project, netbeans will ask you if you want to create it from an existing ant bundle. if not netbeans, eclipse does it.
then compile your project, and once you have a jar, reference it from your projects.

good luck
How will you compile the  an external source code which was not built from the Net Beans IDE . Net beans seems to use its own Ant scripts and it seems to not use the Ant scripts written by the publisher of the code  , How will I override it ?? .  I don't , at the present have Eclipse installed in my comp .

---

