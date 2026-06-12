---
title: "How do I dynamically link"
date: 2010-07-07
forum: Programming Talk
---

### Post by beattyml1 on 2010-07-07
So to start off I am using Qt Creator with QMake

Say I have a header file libMyClass.h and a shared library MyClass.so

MyClass.so is in ../../bin,  MyClass.h is Currently in ../MyClass

libMyClass.so/MyClass.h defines the class MyClass and should (assuming Qt Creator setup the code properly) make it visible in the .so

In the .pro file I have the following code (along with other non-related code):
```

LIBS += ../../bin/libMyClass.so
INCLUDEPATH += ../MyClass

```

In the source file in which I wish to use MyClass I have tried each of the following code segments.
```
#include <MyClass>
```
```
#include <MyClass.h>
```

I have had issues with each would someone be able to provide me with some sort of example code/project/projects that I could use along with a little explanation that I could use to figure out how to do this.

---

### Post by Zugzwang on 2010-07-07
> **beattyml1 said:**
> In the .pro file I have the following code (along with other non-related code):
```

LIBS += ../../bin/libMyClass.so
INCLUDEPATH += ../MyClass

```


I think here is your problem. The variable "LIBS" contains linker options and not libraries to link against. Rather try the following line for "LIBS" instead:
```

LIBS += -L../../bin -lMyClass

```

For your libraries: Try instead:
```

#include "MyClass.h"

```

If it doesn't work, copy&paste the result of running "make" in your project directory.

---

### Post by beattyml1 on 2010-07-07
I think it helped (I've been trying so many things I can't rightly remember what the original error message was).  But I am still getting errors.  The Following was the compile output.

```
Running build steps for project TestProject...
Configuration unchanged, skipping QMake step.
Starting: /usr/bin/make -w 
make: Entering directory `/home/mbeatty/Desktop/Hi/TestProject'
cd FlickableWidgets/ && /usr/bin/make -f Makefile
make[1]: Entering directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets'
cd Flickable/ && /usr/bin/make -f Makefile
make[2]: Entering directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets/Flickable'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets/Flickable'
cd FlickableListView/ && /usr/bin/make -f Makefile
make[2]: Entering directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets/FlickableListView'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets/FlickableListView'
cd FlickableWidgetsPlugins/ && /usr/bin/make -f Makefile
make[2]: Entering directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets/FlickableWidgetsPlugins'
/usr/bin/make -f Makefile.Debug
make[3]: Entering directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets/FlickableWidgetsPlugins'
make[3]: Nothing to be done for `first'.
make[3]: Leaving directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets/FlickableWidgetsPlugins'
make[2]: Leaving directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets/FlickableWidgetsPlugins'
make[1]: Leaving directory `/home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets'
cd TestApplication/ && /usr/bin/make -f Makefile
make[1]: Entering directory `/home/mbeatty/Desktop/Hi/TestProject/TestApplication'
g++ -c -pipe -g -Wall -W -D_REENTRANT -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I../FlickableWidgets/FlickableListView -I. -I. -o widget.o widget.cpp
In file included from ui_widget.h:19,
from widget.cpp:2:
../FlickableWidgets/FlickableListView/flickablelistview.h:5:23: error: flickable.h: No such file or directory
In file included from ui_widget.h:19,
from widget.cpp:2:
../FlickableWidgets/FlickableListView/flickablelistview.h:8: error: expected class-name before ‘{’ token
make[1]: Leaving directory `/home/mbeatty/Desktop/Hi/TestProject/TestApplication'
make[1]: *** [widget.o] Error 1
make: *** [sub-TestApplication-make_default] Error 2
make: Leaving directory `/home/mbeatty/Desktop/Hi/TestProject'
Exited with code 2.
Error while building project TestProject
When executing build step 'Make'
```

I uploaded a copy of the the body of my code in question + a driver to replace the rest of the program to my windows skydrive.  If you check it out open the TestProject.pro file.

---

### Post by dwhitney67 on 2010-07-07
Ok, it appears that 'make' is being executed from this directory: /home/mbeatty/Desktop/Hi/TestProject/TestApplication

Your compiler options seems to indicate that you have header files in /home/mbeatty/Desktop/Hi/TestProject/FlickableWidgets/FlickableListView and in /home/mbeatty/Desktop/Hi/TestProject/TestApplication.

Is one of these areas where the header file flickable.h exists?

If not, then you have a configuration issue with your project (ie .pro file).

---

