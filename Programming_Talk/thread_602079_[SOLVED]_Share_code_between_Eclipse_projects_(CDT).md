---
title: "[SOLVED] Share code between Eclipse projects (CDT)"
date: 2007-11-03
forum: Programming Talk
---

### Post by leohart on 2007-11-03
Hi guys,

Can some Eclipse guru helps me with this. I have two eclipse projects that both use several files (common classes). Is there a way for me to not having to copy and paste stuff around?

---

### Post by CptPicard on 2007-11-03
In the Project Properties (right-click on project name and choose from popup) where you can add jars and and such to classpath, there is also a tab for adding other projects.

EDIT: Oh, sorry, I didn't realize this was about CDT. Anyway, glad you figured it out ;)

---

### Post by leohart on 2007-11-04
Just to keep an update on how I solved this problem.

I followed CptPicard's help
1- Right click my project => choose Properties
2- Under C/C++ Build => Tool Settings => GCC C++ Compiler => Directories
3- Click on the Add button on the right side, then choose where my share files are.

Hit Ok several times. Build the project again. Done :-)

---

