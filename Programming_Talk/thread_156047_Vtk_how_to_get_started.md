---
title: "Vtk: how to get started"
date: 2006-04-06
forum: Programming Talk
---

### Post by swong1 on 2006-04-06
Hi, I wanted to do customized graphical visualization from my c++ program and I decided to try out vtk. I downloaded all the packages related to vtk from synaptic and cmake and try to run some of the example codes and guess what? It didn't work. 

I tried 
```

g++ Cone.cxx                                ---------Couldn't find the header files

g++ -I /usr/include/vtk/ Cone.cxx    -----------/usr/share/ld Cannot open output file: permission denied collect2: ld returned 1 exit status

gcc -I /usr/include/vtk/ Cone.cxx      ------------ same error message as above

g++ -I /usr/include/vtk/ -D /usr/share/vtkdata Cone.cxx -----------<command line>:1:1: error: macro names must be identifiers

cmake .

CMake Error: Error in cmake code at
/usr/share/CMake/Modules/CMakeDetermineSystem.cmake:71:
FILE Internal CMake error when trying to open file: /usr/share/vtk/Tutorial/Step1/Cxx/CMakeOutput.log for writting.
CMake Error: Could not open file for write in copy operation /usr/share/vtk/Tutorial/Step1/Cxx/CMakeSystem.cmake.tmp
CMake Error: Error in cmake code at
/usr/share/CMake/Modules/CMakeDetermineSystem.cmake:75:
CONFIGURE_FILE Problem configuring file
CMake Error: Error in cmake code at
/usr/share/CMake/Modules/CMakeDetermineCCompiler.cmake:62:
FILE Internal CMake error when trying to open file: /usr/share/vtk/Tutorial/Step1/Cxx/CMakeOutput.log for writting.
CMake Error: Could not open file for write in copy operation /usr/share/vtk/Tutorial/Step1/Cxx/CMakeCCompiler.cmake.tmp
CMake Error: Error in cmake code at
/usr/share/CMake/Modules/CMakeDetermineCCompiler.cmake:81:
CONFIGURE_FILE Problem configuring file
CMake Error: Error in cmake code at
/usr/share/CMake/Modules/CMakeDetermineCXXCompiler.cmake:48:
FILE Internal CMake error when trying to open file: /usr/share/vtk/Tutorial/Step1/Cxx/CMakeOutput.log for writting.
CMake Error: Could not open file for write in copy operation /usr/share/vtk/Tutorial/Step1/Cxx/CMakeCXXCompiler.cmake.tmp
CMake Error: Error in cmake code at
/usr/share/CMake/Modules/CMakeDetermineCXXCompiler.cmake:60:
CONFIGURE_FILE Problem configuring file
-- Check for working C compiler: gcc
CMake Error: Error in cmake code at
/usr/share/CMake/Modules/CMakeTestCCompiler.cmake:8:
FILE Internal CMake error when trying to open file: /usr/share/vtk/Tutorial/Step1/Cxx/CMakeTmp/testCCompiler.c for writting.
CMake Error: Failed to create CMakeList file for /usr/share/vtk/Tutorial/Step1/Cxx/CMakeTmp/CMakeLists.txt
-- Check for working C compiler: gcc -- broken
CMake Error: Error in cmake code at
/usr/share/CMake/Modules/CMakeTestCCompiler.cmake:20:
FILE Internal CMake error when trying to open file: /usr/share/vtk/Tutorial/Step1/Cxx/CMakeError.log for writting.
The C compiler "gcc" is not able to compile a simple test program.
It fails with the following output:


CMake will not be able to correctly generate this project.
-- Configuring done
CMake Error: Unable to open cache file for save. /usr/share/vtk/Tutorial/Step1/Cxx/CMakeCache.txt


```

This is as far as I get. What am I missing?

---

### Post by swong1 on 2006-04-07
Okay, after looking at the documentation, here's what I tried:
Since the directories are in the root filesystem, I added "sudo" to enable root access.
```

sudo cmake -i              (and go through the q&a procedure, only change the directory prefix from /usr/local to /usr since all my header and library files are in /usr/include/vtk and /usr/lib/vtk.)

```
cmake successfully generate Makefile and a whole bunch of other cmake files. I run "sudo make" and get the following error message:
```

/usr/bin/ld: cannot find -lpng
collect2: ld returned 1 exit status
make[1]: *** [/usr/share/vtk/Tutorial/Step1/Cxx/Cone] Error 1
make: *** [default_target] Error 2

```
How do I fix the problem? Any help is greatly appreciated.

---

### Post by swong1 on 2006-04-07
Sorry duplicate post.

---

### Post by pitkali on 2006-04-08
That looks like lack of libpng-dev.

Regards,

---

### Post by swong1 on 2006-04-08
I downloaded libpng12-dev and compile again, this time the error message is
```

/usr/bin/ld: cannot find -ljpeg
collect2: ld returned 1 exit status
make[1]: *** [/usr/share/vtk/Tutorial/Step1/Cxx/Cone] Error 1
make: *** [default_target] Error 2

```
I now know what to do. Many thanks pitkali :-)

---

### Post by swong1 on 2006-04-08
After running "sudo make" a few times and downloaded the missing libraries, I was finally able to generate the executable. However, the image appears for a split second and then disappear. Maybe my graphics card is too powerful :-)

---

### Post by rooparam on 2011-02-06
@swong1: same case here, maybe its iMac's powerful GPU .... ;) Change the code (before for loop just type "while(1)" and put "int i" declaration in for loop initializer.

I noticed one thing though, when the ./Cone is running in 300x300 window, it is consuming 58% Core2 Duo CPU, while in Maximized window (1680x1050), it is only consuming 8% CPU power .... [strange]

---

