---
title: "Organization"
date: 2009-04-09
forum: Programming Talk
---

### Post by swappo1 on 2009-04-09
Hello,

My home folder is really filling up with .c and .cpp programs.  I would like to segregate my programs into folders to make things more organized.  However, I don't want to have to type in the path to the file every time I need to compile and/or run a program.  I write my programs in gedit and use gcc/g++ for my compiler.  Is there a to do this that won't make compiling and running a program more typing intensive?  Would and IDE like code::blocs help with this?  Thanks.

---

### Post by tneva82 on 2009-04-09
> **swappo1 said:**
> Hello,

My home folder is really filling up with .c and .cpp programs.  I would like to segregate my programs into folders to make things more organized.  However, I don't want to have to type in the path to the file every time I need to compile and/or run a program.  I write my programs in gedit and use gcc/g++ for my compiler.  Is there a to do this that won't make compiling and running a program more typing intensive?  Would and IDE like code::blocs help with this?  Thanks.

Makefiles? Can't get much easier than typing make after you have created makefile.

---

### Post by swappo1 on 2009-04-09
For a program where I would be creating header files, a Makefile would be fine.  Most of my programs are small and are to work out an idea or concept before I put it into a larger program where I would use a Makefile.  For these, a Makefile would be more typing intensive.

---

### Post by sujoy on 2009-04-09
well with a proper IDE you can open it with a few clicks and just run from the IDE itself.

---

### Post by soltanis on 2009-04-09
My setup is this

~/code/

All my active projects have their own folder there, all inactive/dropped code that I don't want to delete I have in a directory called old.

When I start a coding sessions, I just do cd code/[project]/ (tab completion is great), fire up vi and get to it. For C anyway.

For java, I use netbeans. Java's requirements for file organization are simply too high-maintenance for me to use a terminal on them.

---

### Post by Yannick Le Saint kyncani on 2009-04-09
+1 for a makefile with ~/bin/ install and cleanup rules

---

