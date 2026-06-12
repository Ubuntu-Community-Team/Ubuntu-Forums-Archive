---
title: "Problem with Anjuta"
date: 2008-04-03
forum: Packaging and Compiling Programs
---

### Post by rtkmas on 2008-04-03
Hi, I have a problem with Anjuta.
After I have compiled my c++ source, I make the Execute Program, it asks me for Arguments: I type the compiled file name but it says "Program 'home/rtkmas/file is not a local file"
what can I do?

---

### Post by rebel_angel on 2008-05-01
I'm having the same problem with C. 
it compiles pretty well but when i want to execute it ... i get the exact same error msg. :confused::confused:

---

### Post by rebel_angel on 2008-05-02
problem solved ! anjuta 2.4 requires the user to create a project before executing ( kind of like visual studio 2005 ). If you click the new -> project link, it will show you the packages you will need to install (surprisingly ... i can't remember the name). if the packages are installed, then when you create a new project you will some other errors saying that some packages are still missing. these are libtool, autoconf and the another one i cant remember the name of !!

after that you are all set. in order to debug you have to click the debugger option from the plugins.

**settings --> plugins --> debugger**

happy Coding

---

### Post by rebel_angel on 2008-05-02
**it will show you the packages you will need to install (surprisingly ... i can't remember the name).** --> now i remember ... its ***autogen*** . this is a common package for all IDE

---

