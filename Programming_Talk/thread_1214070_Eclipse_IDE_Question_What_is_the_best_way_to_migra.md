---
title: "Eclipse IDE Question: What is the best way to migrate workspace?"
date: 2009-07-15
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-07-15
I am working on a project with 2 other people and they choose to use the default Eclipse workspace (C:/workspace) and I choose a different directory.  This causes a problem when I include referenced libraries, the paths won't match up.  So I want to move all my projects under C:/workspace.  

1. What's the best way to to do this in Eclipse 3.5?
2. Is there a better, OS independent way of doing this?  I plan to move my development to Ubuntu eventually and at that point, the C:/ paths will break.

---

### Post by dwhitney67 on 2009-07-15
The best way is to define an environment variable that contains the path to your workspace.  For example, WSPACE=C:\M$\Blows\Folder\workspace.

Your Eclipse project file should reference the WSPACE in lieu of hard-coding the paths to the header file and library directories.

---

### Post by SNYP40A1 on 2009-07-22
[http://www.coderanch.com/t/104883/IDEs-Version-Control-other-tools/Java-Relative-Build-Path-Eclipse](http://www.coderanch.com/t/104883/IDEs-Version-Control-other-tools/Java-Relative-Build-Path-Eclipse)

---

