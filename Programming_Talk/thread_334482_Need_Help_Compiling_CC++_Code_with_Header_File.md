---
title: "Need Help Compiling C/C++ Code with Header File"
date: 2007-01-09
forum: Programming Talk
---

### Post by BashMan on 2007-01-09
Hi Everyone,

I am trying to write simple MQI C/C++ example. However, I am unable to compile it. Here is the source code.
========================
// File:   MQTest.cc
// Created on January 8, 2007, 10:01 PM

#include <stdlib.h>
#include <stdio.h>
#include <string.h>

/* includes for MQI */
//#include <cmqc.h>
  
int main(int argc, char** argv) {
    return (EXIT_SUCCESS);
}
========================

When I comment out "#include <cmqc.h>" it compiles successfully. When I uncomment "#include <cmqc.h>" it does not compile. I get the following error:

=====================
Running "C:\cygwin\bin\make.exe -f Makefile CONF=Debug clean" in C:\bash\bashccode\netbeans_c_projects\MQI

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .clean-conf
make[1]: Entering directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQI'
rm -f -r build/Debug
rm -f dist/Debug/GNU-Windows/mqi
make[1]: Leaving directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQI'

Clean successful. Exit value 0.

Running "C:\cygwin\bin\make.exe -f Makefile CONF=Debug" in C:\bash\bashccode\netbeans_c_projects\MQI

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQI'
g++    -c -g -o build/Debug/GNU-Windows/MQTest.o MQTest.cc
MQTest.cc:12:18: cmqc.h: No such file or directory
make[1]: *** [build/Debug/GNU-Windows/MQTest.o] Error 1
make[1]: Leaving directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQI'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.
=====================

I added the "cmqc.h" header file to my project. Righ click on "Header Files" -> "Add Existing Items" and selected the header file. Attempted to recompile and got the same error as above. Any help is greatly appreciated.

Thanks,
BashMan

---

### Post by Wybiral on 2007-01-09
I've never used "MQI"... But theres a good chance the library isn't being linked to it. From the command line it would probably be something like "-lMQI" or "-lmqi" but I'm not sure... But usually when people have a problem compiling with a new library, it's because they aren't linking to it right. You need to make sure the path to "cmqc.h" is in your include path and that you link to the library.

---

### Post by po0f on 2007-01-09
BashMan,

Where is this 'cmqc.h' header file?  If it's in the directory containing the source file, a compile command like this should find it:
```
[FONT="Courier New"]g++ -c -g **-I./** -o build/Debug/GNU-Windows/MQTest.o MQTest.cc[/FONT]
```

g++'s -I switch tells it to also look for header files in the specified directory.  './' should include the directory the source file resides in.


Wybiral,

If you notice, it's not a linking error, it just couldn't find the header file.

---

### Post by gun on 2007-01-09
> **BashMan said:**
> Hi Everyone,

I am trying to write simple MQI C/C++ example. However, I am unable to compile it. Here is the source code.
========================
// File:   MQTest.cc
// Created on January 8, 2007, 10:01 PM

#include <stdlib.h>
#include <stdio.h>
#include <string.h>

/* includes for MQI */
//#include <cmqc.h>
  
int main(int argc, char** argv) {
    return (EXIT_SUCCESS);
}
========================

When I comment out "#include <cmqc.h>" it compiles successfully. When I uncomment "#include <cmqc.h>" it does not compile. I get the following error:

=====================
Running "C:\cygwin\bin\make.exe -f Makefile CONF=Debug clean" in C:\bash\bashccode\netbeans_c_projects\MQI

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .clean-conf
make[1]: Entering directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQI'
rm -f -r build/Debug
rm -f dist/Debug/GNU-Windows/mqi
make[1]: Leaving directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQI'

Clean successful. Exit value 0.

Running "C:\cygwin\bin\make.exe -f Makefile CONF=Debug" in C:\bash\bashccode\netbeans_c_projects\MQI

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQI'
g++    -c -g -o build/Debug/GNU-Windows/MQTest.o MQTest.cc
MQTest.cc:12:18: cmqc.h: No such file or directory
make[1]: *** [build/Debug/GNU-Windows/MQTest.o] Error 1
make[1]: Leaving directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQI'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.
=====================

I added the "cmqc.h" header file to my project. Righ click on "Header Files" -> "Add Existing Items" and selected the header file. Attempted to recompile and got the same error as above. Any help is greatly appreciated.

Thanks,
BashMan
11.000 code 
look up..
[www.unreadedpost.com](www.unreadedpost.com)

---

### Post by BashMan on 2007-01-09
The cmqc.h header file is in

C:\Program Files\IBM\WebSphere MQ\Tools\c\include

---

### Post by BashMan on 2007-01-09
> **po0f said:**
> BashMan,

Where is this 'cmqc.h' header file?  If it's in the directory containing the source file, a compile command like this should find it:
```
[FONT="Courier New"]g++ -c -g **-I./** -o build/Debug/GNU-Windows/MQTest.o MQTest.cc[/FONT]
```

g++'s -I switch tells it to also look for header files in the specified directory.  './' should include the directory the source file resides in.


Wybiral,

If you notice, it's not a linking error, it just couldn't find the header file.



==== 
Hi,

Thanks for the help thus far. The "cmqc.h" reside in:

C:\Program Files\IBM\WebSphere MQ\Tools\c\include
I went to project properties and add the director in which the header file exist and I am still getting the same error.

===================

Running "C:\cygwin\bin\make.exe -f Makefile CONF=Debug clean" in C:\bash\bashccode\netbeans_c_projects\MQBTech

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .clean-conf
make[1]: Entering directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQBTech'
rm -f -r build/Debug
rm -f dist/Debug/GNU-Windows/mqbtech
make[1]: Leaving directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQBTech'

Clean successful. Exit value 0.

Running "C:\cygwin\bin\make.exe -f Makefile CONF=Debug" in C:\bash\bashccode\netbeans_c_projects\MQBTech

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQBTech'
gcc    -c -g -IC:/Program Files/IBM/WebSphere MQ/Tools/c/include -o build/Debug/GNU-Windows/mqtest.o mqtest.c
gcc: Files/IBM/WebSphere: No such file or directory
gcc: MQ/Tools/c/include: No such file or directory
mqtest.c:10:18: cmqc.h: No such file or directory
make[1]: *** [build/Debug/GNU-Windows/mqtest.o] Error 1
make[1]: Leaving directory `/cygdrive/c/bash/bashccode/netbeans_c_projects/MQBTech'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.
=================

It cannot find any of the directories.

gcc: Files/IBM/WebSphere: No such file or directory
gcc: MQ/Tools/c/include: No such file or directory
mqtest.c:10:18: cmqc.h: No such file or directory


Is it something wrong with the path ?

Thanks,

BashMan

---

### Post by po0f on 2007-01-09
BashMan,

I don't know exactly which characters are special characters on Windows, but try this as the directory:
```
[FONT="Courier New"]C:\Program**\** Files\IBM\WebSphere**\** MQ\Tools\c\include[/FONT]
```

Since it *could* find C:\Program as a directory (read the errors carefully), we can be fairly certain it's barfing on the spaces.  What I posted above escapes all the spaces in the directory path.  Hopefully it will work.

---

