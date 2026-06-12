---
title: "QT Won't Compile"
date: 2009-06-21
forum: Packaging and Compiling Programs
---

### Post by DGortze380 on 2009-06-21
Hey All.

I'm running into an issue I just can't seem to sort out. 
I'm sure it's just a configuration error on my part.

I have a fresh install of QT4 on my MacBook (currently using OS X, going to try to duplicate the problem in Ubuntu now).

When trying to compile the simple qmake example provided with package, a get a number of errors...


When trying to use qmake via the commandline:
I create a .pro file
I run: qmake -o Makefile hello.pro
The directory Makefile.xcodeprj is created, as well as Info.plist
I run: make
I get the error: make: *** No targets specified and no makefile found.  Stop.
According to the qmake tutorial, a Makefile should have been created.

So from here I figure, I have an xcode project file, great. I can use xcode to compile. Wrong.

Opening the xcode project and trying to compile results in the following error:     
```

Linking /Developer/Examples/Qt/qmake/tutorial/build/Debug/hello.app/Contents/MacOS/hello 

/usr/bin/ld: /Library/Frameworks/QtGui.framework/QtGui load command 6 unknown cmd field

/usr/bin/ld: /Library/Frameworks/QtCore.framework/QtCore load command 5 unknown cmd field

Command /usr/bin/g++-4.0 failed with exit code 1

```


Ok, so no xcode. 
I open the project in QT Creator and get the following error when trying to build.

collect2: ld returned 1 exit status

here's the compiler output

```

Running build steps for project hello...
Starting: /usr/bin/qmake /Developer/Examples/Qt/qmake/tutorial/hello.pro -spec macx-g++ -r 
Exited with code 0.
Starting: /usr/bin/make -w 
make: Entering directory `/Developer/Examples/Qt/qmake/tutorial'
g++ -c -pipe -g -gdwarf-2 -Wall -W -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/local/Qt4.5/mkspecs/macx-g++ -I. -I/Library/Frameworks/QtCore.framework/Versions/4/Headers -I/usr/include/QtCore -I/Library/Frameworks/QtGui.framework/Versions/4/Headers -I/usr/include/QtGui -I/usr/include -I. -I. -F/Library/Frameworks -o hello.o hello.cpp
g++ -c -pipe -g -gdwarf-2 -Wall -W -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/local/Qt4.5/mkspecs/macx-g++ -I. -I/Library/Frameworks/QtCore.framework/Versions/4/Headers -I/usr/include/QtCore -I/Library/Frameworks/QtGui.framework/Versions/4/Headers -I/usr/include/QtGui -I/usr/include -I. -I. -F/Library/Frameworks -o main.o main.cpp
g++ -headerpad_max_install_names -o hello.app/Contents/MacOS/hello hello.o main.o -F/Library/Frameworks -L/Library/Frameworks -framework QtGui -framework Carbon -framework AppKit -framework QtCore -lz -lm -framework ApplicationServices
/usr/bin/ld: /Library/Frameworks/QtGui.framework/QtGui load command 6 unknown cmd field
/usr/bin/ld: /Library/Frameworks/QtCore.framework/QtCore load command 5 unknown cmd field
collect2: ld returned 1 exit status
make: *** [hello.app/Contents/MacOS/hello] Error 1
make: Leaving directory `/Developer/Examples/Qt/qmake/tutorial'
Exited with code 2.
Error while building project hello
When executing build step 'Make'

```

All these seem to go back to a problem with my non-existent make file, which makes sense. But how the hell do I fix it??

---

