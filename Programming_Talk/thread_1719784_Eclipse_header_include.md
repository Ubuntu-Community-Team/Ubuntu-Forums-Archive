---
title: "Eclipse header include"
date: 2011-04-02
forum: Programming Talk
---

### Post by skashar on 2011-04-02
I have problems with including header files in Eclipse project. There are header files in 
subfolders and sub-subfolders. Every time I have to add, I must to C/C++ General => Paths and Symbols => GNU C++ and then Add...

Is there any way to include all the subdirectories in an easer way?

---

### Post by dwhitney67 on 2011-04-02
> **skashar said:**
> 
Is there any way to include all the subdirectories in an easer way?

No, there is not.  Of course, there is nothing stopping you from placing all of your header files in one directory.  But some developers do not like this approach; thus they organize their header files to be as close to the implementation file (whether .c or .cpp) as possible.

---

