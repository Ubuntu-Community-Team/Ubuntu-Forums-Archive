---
title: "Perl/Python Running Help"
date: 2006-08-19
forum: Programming Talk
---

### Post by Samurai Cal on 2006-08-19
Hey I'm trying to run perl/python programs that i make, so I open gedit and write down some simple script, and save it as .pl or .py, whatever floats my boat at the time (yes I remember the shabang line in perl).  Then I open up the home folder and drag the program into terminal and press enter (in other words i type "/home/cal/hello.pl"), and it comes back with the error:

bash: /home/cal/hello.pl: Permission denied

This happens with both perl and python, and I have installed interpreters for both and I'm 100% sure they're in the proper directories.  What's this shenanigans about?

---

### Post by reacocard on 2006-08-19
right-click the file, choose 'properties'. under 'permissions', check your execute box (upper right of the nine). now try running it.

---

### Post by nephish on 2006-08-19
or do it from a terminal.

if your file is named myfile.py do this
```

chmod a+x myfile.py 

```

---

### Post by chonger on 2006-08-21
> **Samurai Cal said:**
> Hey I'm trying to run perl/python programs that i make, so I open gedit and write down some simple script, and save it as .pl or .py, whatever floats my boat at the time (yes I remember the shabang line in perl).  Then I open up the home folder and drag the program into terminal and press enter (in other words i type "/home/cal/hello.pl"), and it comes back with the error:

bash: /home/cal/hello.pl: Permission denied

This happens with both perl and python, and I have installed interpreters for both and I'm 100% sure they're in the proper directories.  What's this shenanigans about?

Unix files have "executable" permissions:

[http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)

---

