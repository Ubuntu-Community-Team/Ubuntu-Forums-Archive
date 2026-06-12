---
title: "fortran/c++ programs"
date: 2010-04-14
forum: Programming Talk
---

### Post by farside bunny on 2010-04-14
Hi Every one!
sorry for the noob question ,but i was wondering/looking for recommendation for a work environment/ide for fortran and c/c++ i have tired using netbean but after a while and on big projects its gets heavy and sluggish.
also i have recently learned that you can link fortran and cpp programs together will such a program be able to support such a thing ?
thanks a lot in advance and sorry for the silly question 
         Bunny

---

### Post by MadCow108 on 2010-04-14
if netbeans is to heavy for you consider geany.
It is very minimal but still quite capable. Also it is very fast.
But you have less advanced features than with netbeans.
Especially you'll have to accustom yourself with makefiles to build complex programs.

Alternative heavyweight IDE's would be Eclipse or Code::Blocks

The more sophisticated IDE's should support linking of fortran and C++ without too much makefile hacking.
Worst case is that you have to make two projects one for fortran and one for c++ and then just pass appropriate link flags to join the binaries in one of the projects.
(I have never done that in and IDE myself, so I can't help further)

---

### Post by farside bunny on 2010-04-14
thanks !!
netbeans becomes heavy after a certain while its open or when a lot of tabs are open ,i think i might have some sort of problem with the java 
but i will try code block as well

---

