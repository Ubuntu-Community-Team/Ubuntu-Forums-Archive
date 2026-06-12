---
title: "Qt Problem in OpenTLD"
date: 2012-10-25
forum: Programming Talk
---

### Post by Ibrahim mufeed on 2012-10-25
Hi all,

I have downloaded a software package (OpenTLD) and installed it on my Ubuntu using the steps provided and it worked just fine. Now I want to edit this package using Eclipse.

When I try to execute "Build All" from the "Project" menu in Eclipse it returns this error:

```

Building file: ../src/opentld/qopentld/ConfigDialog.cpp
Invoking: Cross G++ Compiler
g++ -I/usr/include/qt4 -I/usr/include/qt4/QtGui -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/opentld/qopentld/ConfigDialog.d" -MT"src/opentld/qopentld/ConfigDialog.d" -o "src/opentld/qopentld/ConfigDialog.o" "../src/opentld/qopentld/ConfigDialog.cpp"
In file included from ../src/opentld/qopentld/ConfigDialog.cpp:20:0:
../src/opentld/qopentld/ConfigDialog.h:31:29: fatal error: ui_ConfigDialog.h: No such file or directory
compilation terminated.
make: *** [src/opentld/qopentld/ConfigDialog.o] Error 1

```

I have searched for a solution online but I could not find anything helpful. Any idea?!

Thanks in advance.
Ibrahim

---

### Post by spjackson on 2012-10-25
I don't know how you configure eclipse to do this but... in Makefile terms you need a rule like this:
```

ui_ConfigDialog.h: ConfigDialog.ui
     uic ConfigDialog.ui -o ui_ConfigDialog.h

```
I hope that points you in the right direction.

---

### Post by Ibrahim mufeed on 2012-10-25
Thank you for your reply. Actually I copied the files and made a new empty Eclipse project out of it.

I do not know how to make the rule in the Makefile as it is auto-generated. I tried with the settings of the project but still not solved!

Regards,

---

### Post by spjackson on 2012-10-25
> 
Actually I copied the files and made a new empty Eclipse project out of it.

I have done a lot of work with Qt. I have done only a little work with Eclipse, and most of that has been Java. I haven't previously used Eclipse for a Qt project.

I've taken an existing project, run qmake to generate a Makefile, then in Eclipse File->New->Makefile Project with Existing Code. This works, successfully generating ui_*.h files and compiling code that runs.

I am aware that there is such a thing as Qt Eclipse integration, but I haven't tried it.

It seems to me that creating an empty project and having to tell Eclipse how to build the target using custom rules is more complicated than either using the generated Makefile, or using Qt Eclipse integration. This might be a good route for an Eclipse expert, but I'm not one, so I don't think I can help with that I'm afraid.

---

### Post by Ibrahim mufeed on 2012-10-25
Finally I solved the issue. I learned how to use CMake with Eclipse and it worked! Thank you for your reply, it was helpful.

Regards,

---

