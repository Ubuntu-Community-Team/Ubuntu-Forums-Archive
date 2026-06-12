---
title: "Linker error: undefined reference to symbol 'glClear'"
date: 2014-11-29
forum: Programming Talk
---

### Post by manu-brotz on 2014-11-29
Hello

I am trying to compile an application but i get a linking error.
This is the application: [https://github.com/GhengopelALPHA/scriptbots](https://github.com/GhengopelALPHA/scriptbots)
More info: [https://sites.google.com/site/scriptbotsevo/home](https://sites.google.com/site/scriptbotsevo/home)

The errors pop up when i issue the **make** command.

Since i have no experience in c++, i have absolutely no clue what to do about this.
Google spits out lots of advice for similar problems, but so far nothing has worked...

Any help is appreciated!

Thank you very much.

M. Brotz

The command **cmake ../** works fine:
```

-- The C compiler identification is GNU 4.8.2
-- The CXX compiler identification is GNU 4.8.2
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for XOpenDisplay in /usr/lib/x86_64-linux-gnu/libX11.so;/usr/lib/x86_64-linux-gnu/libXext.so
-- Looking for XOpenDisplay in /usr/lib/x86_64-linux-gnu/libX11.so;/usr/lib/x86_64-linux-gnu/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Found X11: /usr/lib/x86_64-linux-gnu/libX11.so
-- Found OpenGL: /usr/lib/x86_64-linux-gnu/libGL.so  
-- Found GLUT: /usr/lib/x86_64-linux-gnu/libglut.so  
-- Try OpenMP C flag = [-fopenmp]
-- Performing Test OpenMP_FLAG_DETECTED
-- Performing Test OpenMP_FLAG_DETECTED - Success
-- Try OpenMP CXX flag = [-fopenmp]
-- Performing Test OpenMP_FLAG_DETECTED
-- Performing Test OpenMP_FLAG_DETECTED - Success
-- Found OpenMP: -fopenmp  
-- Configuring done
-- Generating done
-- Build files have been written to: /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/build

```

But the command **make** gives me the following error:
```

Scanning dependencies of target scriptbots
[ 10%] Building CXX object CMakeFiles/scriptbots.dir/ReadWrite.cpp.o
In file included from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glui.h:54:0,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/GLView.h:7,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/ReadWrite.h:6,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/ReadWrite.cpp:33:
/home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glut.h:63:0: warning: "APIENTRY" redefined [enabled by default]
 #define APIENTRY
 ^
In file included from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glut.h:58:0,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glui.h:54,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/GLView.h:7,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/ReadWrite.h:6,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/ReadWrite.cpp:33:
/usr/include/GL/gl.h:88:0: note: this is the location of the previous definition
 #define APIENTRY GLAPIENTRY
 ^
[ 20%] Building CXX object CMakeFiles/scriptbots.dir/View.cpp.o
[ 30%] Building CXX object CMakeFiles/scriptbots.dir/GLView.cpp.o
In file included from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glui.h:54:0,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/GLView.h:7,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/GLView.cpp:1:
/home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glut.h:63:0: warning: "APIENTRY" redefined [enabled by default]
 #define APIENTRY
 ^
In file included from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glut.h:58:0,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glui.h:54,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/GLView.h:7,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/GLView.cpp:1:
/usr/include/GL/gl.h:88:0: note: this is the location of the previous definition
 #define APIENTRY GLAPIENTRY
 ^
[ 40%] Building CXX object CMakeFiles/scriptbots.dir/main.cpp.o
In file included from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glui.h:54:0,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/GLView.h:7,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/main.cpp:1:
/home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glut.h:63:0: warning: "APIENTRY" redefined [enabled by default]
 #define APIENTRY
 ^
In file included from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glut.h:58:0,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/glui.h:54,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/GLView.h:7,
                 from /home/mbrotz/Entwicklung/cpp/scriptbots/Julian_Hershey/main.cpp:1:
/usr/include/GL/gl.h:88:0: note: this is the location of the previous definition
 #define APIENTRY GLAPIENTRY
 ^
[ 50%] Building CXX object CMakeFiles/scriptbots.dir/DWRAONBrain.cpp.o
[ 60%] Building CXX object CMakeFiles/scriptbots.dir/MLPBrain.cpp.o
[ 70%] Building CXX object CMakeFiles/scriptbots.dir/AssemblyBrain.cpp.o
[ 80%] Building CXX object CMakeFiles/scriptbots.dir/Agent.cpp.o
[ 90%] Building CXX object CMakeFiles/scriptbots.dir/World.cpp.o
[100%] Building CXX object CMakeFiles/scriptbots.dir/vmath.cpp.o
Linking CXX executable scriptbots
/usr/bin/ld: CMakeFiles/scriptbots.dir/GLView.cpp.o: undefined reference to symbol 'glClear'
//usr/lib/nvidia-331/libGL.so.1: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
make[2]: *** [scriptbots] Error 1
make[1]: *** [CMakeFiles/scriptbots.dir/all] Error 2
make: *** [all] Error 2

```

---

### Post by jhay2 on 2014-11-29
you dont have a glut development files download it sudo apt-get install freeglut3-dev

---

### Post by manu-brotz on 2014-11-29
Thank you for your quick answer!
Unfortunately i've already installed the newest version of freeglut3-dev...

---

### Post by jhay2 on 2014-11-29
if so maybe try to create a shell script file and using g++ function build those files using the shell script file 


#!/bin/bash

g++ ./path/to/files.cpp ./path/to/allfile.cpp  -o outputfile -lGL -lglut  

then set the permission of your file to 777  then execute it 

make sure all cpp files are listed on g++ ./path/to/allfile.cpp  before the output file


example i have main.cpp another.cpp lib.cpp i will compile it on a single executable file

g++ main.cpp another.cpp lib.cpp  -o myexecutable -lGL -lglut

---

