---
title: "Need Help Setting Up Hla"
date: 2005-07-24
forum: Programming Talk
---

### Post by grofaz on 2005-07-24
Hi,

Does anyone here know how to set up HLA (High Level Assembly) for Linux, specifically   for ubuntu ??

I'm having a hard time. Appreciate any help. Thanks!

---

### Post by grofaz on 2005-07-25
OK, I'm getting there. I know how to run it now, only the hard way. How do you edit paths in the .bashrc file ?? I need to add some paths to the hla compiler, libraries, and include files to the .bashrc so I don't have to type in the full path everytime I want to run hla. The hla instructions tell me what to do but I don't see the paths directory in the .bashrc they refer to. Anyone? HELP!

---

### Post by DarkW0lf on 2006-03-31
You have to add the path statement, seems most distros don't put it in the .bashrc file anymore.

[http://www.geocities.com/kahlinor/HLA.html](http://www.geocities.com/kahlinor/HLA.html)

You find a great utility here called khla that will take care of the setup for you.
But you will have to still add a path statement that points to this program.
Just add the path statement at the bottom of .bashrc like the documentation shows you and put khla in the same directory (trust me it's easier with khla).

---

