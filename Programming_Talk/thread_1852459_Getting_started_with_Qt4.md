---
title: "Getting started with Qt4"
date: 2011-09-30
forum: Programming Talk
---

### Post by Lars Noodén on 2011-09-30
I have installed libqt4-dev and have the following line in some C++ code:

#include <QApplication>

But upon compilation I get the error, "QtApplication: No such file or directory"

How do I get the compiler to find QtApplications?

---

### Post by hakermania on 2011-09-30
Hello Lars, I'd recommend use of qmake and specify the libraries through the project file (it needs only a QT += gui in your occasion), instead, if you are experienced enough with linking you can download qt creator, do a 
```
qmake -project
``` in the directory of your source code and then open the generated .pro file with QtCreator, it will take care of the rest.

Generally, if you don't want the IDE, the compilation goes like:
```

cd /dir/to/source
qmake -project #generate the project file depending on the source available in the dir
qmake *.pro #generate the Makefile
make #start the compilation following rules on Makefile

```

---

### Post by Lars Noodén on 2011-09-30
QtCreator seems a little complex, tiled and not quite as solid as one might wish. (It crashed)  

Is there another option with a smaller learning curve?

---

### Post by karlson on 2011-09-30
> **Lars Noodén said:**
> QtCreator seems a little complex, tiled and not quite as solid as one might wish. (It crashed)  

Is there another option with a smaller learning curve?

I don't use QtCreator but I do use designer, qmake, uic.  designer is very stable at least for me.

One thing I would try to make sure is exactly which versions of the tools you have since qt3 may be installed it may be pointing to the ones coming from that.

---

### Post by Lars Noodén on 2011-09-30
I've got only the versions with Qt4, no Qt3 anywhere.

---

### Post by hakermania on 2011-09-30
QtCreator is soooo stable, really, never crashed to me 2 years now both used in 10.10, 11.04 and 11.10 and I've done thousands of compilations with it and made hundreds of small or bigger programs.

Qt isn't complex at all, the logic is simple: 
You have the source, then you run qmake -project so as to generate a .pro file. There you can specify anything you want to be done in your makefile in a simple format, for example, there you specify the executable's name via the 'TARGET = NAME', the files that have to be installed etc. Usually in order to simply compile something you will need only to optionally change the TARGET name. Then, you run qmake *.pro which will see what you have specified in your .pro file and it will generate a corresponding Makefile. Then, as usually, you run 'make' to compile from source.
In general, Qt is rather simple; and if you get used to it you'll see that it saves you too much time and effort.

---

### Post by snip3r8 on 2011-10-01
Qt Creator is amazingly stable and amazing in general,I would go so far to say it is the Best cross platform C++ IDE I have ever used

---

