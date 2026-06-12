---
title: "CMake creates bigger executable than plain make"
date: 2012-02-19
forum: Programming Talk
---

### Post by t1497f35 on 2012-02-19
Hi,
The same source code compiled with cmake and make is attached. CMake's executable is like 530 kb, make's one is like 470 kb. **Anyone knows why**?

How to test:
CMake: go to "bin" dir and run "cmake .." then "make"
Make: from root dir of the project type "make"


EDIT: for the code to actually compile libgtkmm-3.0-dev must be installed.

---

### Post by Arndt on 2012-02-19
> **t1497f35 said:**
> Hi,
The same source code compiled with cmake and make is attached. CMake's executable is like 530 kb, make's one is like 470 kb. **Anyone knows why**?

How to test:
CMake: go to "bin" dir and run "cmake .." then "make"
Make: from root dir of the project type "make"


EDIT: for the code to actually compile libgtkmm-3.0-dev must be installed.

What are the actual linking commands in the two cases?

---

### Post by nebukadnezzar on 2012-02-21
That's because CMake defaults to debug mode (as in, it adds -g to gcc, or whichever compiler you are using).

Use 'cmake -DCMAKE_BUILD_TYPE=Release' when invoking cmake (or change it via cmake-gui).

---

### Post by t1497f35 on 2012-02-21
Thanks, however after I run
**cmake -DCMAKE_BUILD_TYPE='Release' ..** and **make**
I still get the same approx. 60 kb file size increase compared to the plain makefile solution.
Using Ubuntu 11.10 amd64.

---

### Post by SevenMachines on 2012-02-21
Looking at running cmake with 
```
 $ make VERBOSE=1
```shows its passing -rdynamic to the linker, whereas the straight make version does not. Therefore, from man gcc
> This instructs the linker to add all symbols, not only used ones, to the dynamic symbol table.That might be worth a look

---

### Post by t1497f35 on 2012-02-21
Thanks a lot, it works!
I added SET(CMAKE_SHARED_LIBRARY_LINK_CXX_FLAGS "") (since this seems to disable -rdynamic) to the main CMakeLists.txt file and the app size is fine now without even specifying the build type as "release"!

---

