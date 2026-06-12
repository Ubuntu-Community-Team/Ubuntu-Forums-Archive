---
title: "c++ linking problem on ubuntu 12.04"
date: 2013-12-17
forum: Programming Talk
---

### Post by melaine.gautier on 2013-12-17
Hello,

I already posted about my problem and solved it with ubuntu 13.04 but I needed to come back to Ubuntu 12.04 for a professionnal installation and my problem appear again, with no solution working.
I can give you a short example if you want to try the compilation on your machine (zip).

My problem come with the linking with scilab. I'm using CMake and had problem with the order of linking and file in the command line and that why I added the option -Wl,--no-as-needed but I seem not working with ubuntu 12.04 :(
c++ version is  4.6.3

```

/usr/bin/c++   -Wall -Wextra -Wl,--no-as-needed -O3 -DNDEBUG -o testScilab   CMakeFiles/testScilab.dir/scilab-lowlevel.cpp.o CMakeFiles/testScilab.dir/scilab.cpp.o CMakeFiles/testScilab.dir/main.cpp.o  /usr/local/lib/scilab/libscilab.so  /usr/local/lib/scilab/libscicall_scilab.so
CMakeFiles/testScilab.dir/scilab-lowlevel.cpp.o: In function `ScilabReadDouble(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, double&)':
scilab-lowlevel.cpp:(.text+0xbc): undefined reference to `pvApiCtx'
scilab-lowlevel.cpp:(.text+0xc7): undefined reference to `isNamedDoubleType'
scilab-lowlevel.cpp:(.text+0x10b): undefined reference to `pvApiCtx'
scilab-lowlevel.cpp:(.text+0x116): undefined reference to `getNamedScalarDouble'
/usr/local/lib/scilab/libscicall_scilab.so: undefined reference to `com_'
/usr/local/lib/scilab/libscicall_scilab.so: undefined reference to `callFunctionFromGateway'
/usr/local/lib/scilab/libscicall_scilab.so: undefined reference to `createNamedMatrixOfString'
/usr/local/lib/scilab/libscicall_scilab.so: undefined reference to `getNamedVarType'
/usr/local/lib/scilab/libscicall_scilab.so: undefined reference to `clearInternalLastError'
/usr/local/lib/scilab/libscicall_scilab.so: undefined reference to `checklhs_'
/usr/local/lib/scilab/libscicall_scilab.so: undefined reference to `freeArrayOfString'
...
```

If I don't add the lib /usr/local/lib/scilab/libscicall_scilab.so, the compiler ask me to add it to get the reference to getNamedScalarDouble
```

 /usr/bin/c++   -Wall -Wextra -Wl,--no-as-needed -O3 -DNDEBUG -o testScilab   CMakeFiles/testScilab.dir/scilab-lowlevel.cpp.o CMakeFiles/testScilab.dir/scilab.cpp.o CMakeFiles/testScilab.dir/main.cpp.o  /usr/local/lib/scilab/libscilab.so  /usr/local/lib/scilab/libscicall_scilab.so /usr/local/lib/scilab/libmat.so
/usr/bin/ld: CMakeFiles/testScilab.dir/scilab-lowlevel.cpp.o: undefined reference to symbol 'getNamedScalarDouble'
/usr/bin/ld: note: 'getNamedScalarDouble' is defined in DSO /usr/local/lib/scilab/libsciapi_scilab.so.5 so try adding it to the linker command line
/usr/local/lib/scilab/libsciapi_scilab.so.5: could not read symbols: Invalid operation

```

I also tried to chang the order of the libraries without succes. 

I need help, a solution, an hint,...
Thanks,
Mélaine

---

### Post by ju2wheels on 2013-12-18
Did you try installing scilab-include from the standard repository?

---

### Post by melaine.gautier on 2013-12-18
Yes, I tried first with the standard installation (default package) and got the same erro then I tried with a local compilation (./configure then make and sudo make install), with scilab version 5.3.3 (same as with the standard) and 5.4.1
without success :-(

---

### Post by steeldriver on 2013-12-18
Can you give us some context of what you are trying to do? it looks like you are trying to use the scilab C/C++ API to incorporate scilab functionality into a custom C/C++ application. If so, is it your own application? or a 3rd party one downloaded from somewhere?

---

### Post by ju2wheels on 2013-12-18
[http://help.scilab.org/docs/5.3.2/en_US/compile_and_run_call_scilab.html](http://help.scilab.org/docs/5.3.2/en_US/compile_and_run_call_scilab.html)

Looks like you are missing the proper linker flags, see the examples there.

---

### Post by ju2wheels on 2013-12-18
I dont have an example to compile, but on my machine, I did the following:

Install from standard repo:

scilab
scilab-include
libxml2
libxml2-dev
libpcre++-dev

Use pkg-config to get the needed scilab compile/link flags:

pkg-config --libs --cflags scilab

Which gave me:

-lieee -lSM -lncurses -ltk8.4 -ltcl8.4 -ldl -I/usr/include/libxml2 -I/usr/include/scilab  -L/usr/lib/scilab -lscilab -lxml2 -lpcre

---

### Post by melaine.gautier on 2013-12-18
Of course Steeldriver, I'm developping an application which use scilab to do the differencial computation. So I include scilab in my project (it was working perfectly until version 12.04, recently I tried 13.X and got the same problem then found a solution by adding the line  -Wl,--no-as-needed in the compilation option - I'm using CMake to generate the makefile). So it's my application which try to link with scilab C/C++ API
When I got the problem, I created a small application (simple call to scilab to see if I can compile or not) but got the same result. I could send you the code if you want to try.

Thank ju2wheels, I tried what you proposed ( I needed to install libpcre++-dev, tk8.4-dev tcl8.4-dev) but I'm still getting the same error. I needed to add -l**scicall_scilab** (which look like the librariy which gets a problem) but pkg-config is not working with it :
pkg-config --libs --cflags scicall_scilab
Package scicall_scilab was not found in the pkg-config search path.
Perhaps you should add the directory containing `scicall_scilab.pc'
to the PKG_CONFIG_PATH environment variable
No package 'scicall_scilab' found

(I also tried with the full path  pkg-config --libs --cflags /usr/local/lib/scilab/libscicall_scilab.so with the same result)

---

### Post by ju2wheels on 2013-12-18
OK I went and grabbed the example simple_call_scilab.c demo script from scilab git repo, and then ran into the exact same issues you did. I did the following to fix it.

1. I installed a few more required packages:

libncurses5 tk-dev libncurses5-dev tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev

2. I changed the includes on the simple_call_scilab.c from the local include:
```
#include "call_scilab.h"
```

to include from the standard system include lib:
```
#include <scilab/call_scilab.h>
```

3. Then I effectively linked it against everything under the sun for scilab and it worked (note the -Wl,--no-as-needed is required as well or it fails):
```
g++ -Wall -Wl,--no-as-needed -o simple_call_scilab.exe $(pkg-config --libs --cflags scilab) $(ls /usr/lib/scilab/ | sed 's/^lib/-l/g' | sed "s/\.so.*$//g" | sort | uniq | grep -v disable) simple_call_scilab.c
```

Hopefully some of that applies to your app as well.

FYI, if your scilab libs are in /usr/local its probably compiling against a manually compiled version and not the default version installed from the repos...

---

### Post by melaine.gautier on 2013-12-19
Thank for the help but It didn't succeed :-( 
I needed to change you compile line adding "grep -v lib" otherwise it was keeping lib* file  (strange because even if I'm not an expert of sed, the line sed 's/^lib/-l/g' should have replace all the "lib" by "-l", isn't it?

also try for a first time with the same file than you and got an error with : scigraphics (I don't care of the graphic part but...)
```
 g++ -Wall -Wl,--no-as-needed -o simple_call_scilab.exe $(pkg-config --libs --cflags scilab) $(ls /usr/lib/scilab/ | sed 's/^lib/-l/g' | sed "s/\.so.*$//g" | sort | uniq | grep -v disable|grep -v lib) simple_call_scilab.c
simple_call_scilab.c: In function ‘int main()’:
simple_call_scilab.c:24:42: warning: passing NULL to non-pointer argument 3 of ‘BOOL StartScilab(char*, char*, int)’ [-Wconversion-null]
simple_call_scilab.c:33:52: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
simple_call_scilab.c:34:33: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
simple_call_scilab.c:35:39: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `cloneGraphicObject'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `buildFigureMenuBar'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `sciGetNbFigure'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `sciGetFiguresId'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `setCurrentObject'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `getFigureModel'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `setGraphicObjectProperty'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `releaseGraphicObjectProperty'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `setAxesModel'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `getAxesModel'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `getConsoleIdentifier'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `setGraphicObjectRelationship'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `createGraphicObject'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `createDataObject'
/usr/local/lib/scilab/libscigraphic_export.so: undefined reference to `deleteGraphicObject'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `getCurrentSubWin'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `getCurrentObject'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `getCurrentFigure'
/usr/local/lib/scilab/libscigraphic_export.so: undefined reference to `ScilabView::getCurrentFigure()'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `setCurrentSubWin'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `setFigureModel'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `getHandle'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `setCurrentFigure'
/usr/local/lib/scilab/libscigraphic_export.so: undefined reference to `getObjectFromHandle'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `registerToController'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `deleteDataObject'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `constructRectangles'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `isAxesModel'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `unregisterToController'
/usr/local/lib/scilab/libscigraphics.so: undefined reference to `isCurrentFigure'
/usr/local/lib/scilab/libscigraphic_export.so: undefined reference to `getGraphicObjectProperty'
collect2: ld returned 1 exit status

```

I tried with the manually compiled version also but got an other error :
```
g++ -Wall -Wl,--no-as-needed -o simple_call_scilab.exe $(pkg-config --libs --cflags scilab) $(ls /usr/local/lib/scilab/ | sed 's/^lib/-l/g' | sed "s/\.so.*$//g" | sort | uniq | grep -v disable|grep -v lib) simple_call_scilab.c
simple_call_scilab.c: In function ‘int main()’:
simple_call_scilab.c:24:42: warning: passing NULL to non-pointer argument 3 of ‘BOOL StartScilab(char*, char*, int)’ [-Wconversion-null]
simple_call_scilab.c:33:52: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
simple_call_scilab.c:34:33: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
simple_call_scilab.c:35:39: warning: deprecated conversion from string constant to ‘char*’ [-Wwrite-strings]
/tmp/cc5PRtT1.o: In function `main':
simple_call_scilab.c:(.text+0x46): undefined reference to `StartScilab'
simple_call_scilab.c:(.text+0x7e): undefined reference to `SendScilabJob'
simple_call_scilab.c:(.text+0x88): undefined reference to `SendScilabJob'
simple_call_scilab.c:(.text+0x92): undefined reference to `SendScilabJob'
simple_call_scilab.c:(.text+0x9c): undefined reference to `TerminateScilab'
collect2: ld returned 1 exit status

```

Thank again for the time you're taking for helping me.

PS : yes I have 2 versions : the manualy compiled in /usr/local and the default one in /usr

---

### Post by melaine.gautier on 2013-12-19
Here is the list of the element from command to add 

```

 ls /usr/lib/scilab/ | sed 's/^lib/-l/g' | sed "s/\.so.*$//g" | sort | uniq | grep -v disable|grep -v lib
-lmat
-lmex
-lmx
-lsciaction_binding
-lsciapi_scilab
-lsciarnoldi
-lsciboolean
-lscicacsd
-lscicall_scilab
-lscicommons
-lscicompletion
-lsciconsole
-lscicore
-lscidata_structures
-lscidifferential_equations
-lscidouble
-lscidoublylinkedlist
-lscidynamic_link
-lscielementary_functions
-lscifftw
-lscifileio
-lscifunctions
-lscigraphic_export
-lscigraphics
-lscigui
-lscihashtable
-lscihdf5
-lscihdf5-forceload
-lscihelptools
-lscihistory_browser
-lscihistory_manager
-lsciinteger
-lsciinterpolation
-lsciintersci
-lsciio
-lscijvm
-lscilab
-lscilab-cli
-lscilinear_algebra
-lscilocalization
-lscimalloc
-lscimatio
-lscioptimization
-lscioutput_stream
-lsciparallel
-lsciparameters
-lscipolynomials
-lscipvm
-lscirenderer
-lsciscicos
-lsciscicos_blocks
-lsciscinotes
-lscishell
-lscisignal_processing
-lscisound
-lscisparse
-lscispecial_functions
-lscispreadsheet
-lscistatistics
-lscistring
-lscisundials
-lscisymbolic
-lscitclsci
-lscitime
-lsciui_data
-lsciumfpack
-lsciwindows_tools
-lscixcos

```

This error is making me crazy

---

### Post by ju2wheels on 2013-12-19
You only have 68 libs in that list, I get 71 on my end:

```

ls /usr/lib/scilab/ | sed 's/^lib/-l/g' | sed "s/\.so.*$//g" | sort | uniq | grep -v disable
-lmat
-lmex
-lmx
-lsciaction_binding
-lsciapi_scilab
-lsciarnoldi
-lsciboolean
-lscicacsd
-lscicall_scilab
-lscicommons
-lscicompletion
-lsciconsole
-lscicore
-lscidata_structures
-lscidifferential_equations
-lscidouble
-lscidoublylinkedlist
-lscidynamiclibrary
-lscidynamic_link
-lscielementary_functions
-lscifftw
-lscifileio
-lscifunctions
-lscigraphic_export
-lscigraphics
-lscigui
-lscihashtable
-lscihdf5
-lscihdf5-forceload
-lscihelptools
-lscihistory_browser
-lscihistory_manager
-lsciinteger
-lsciinterpolation
-lsciintersci
-lsciio
-lscijvm
-lscilab
-lscilab-cli
-lscilibst
-lscilinear_algebra
-lscilocalization
-lscimalloc
-lscimatio
-lscioptimization
-lscioutput_stream
-lsciparallel
-lsciparameters
-lscipolynomials
-lscipvm
-lscirandlib
-lscirenderer
-lsciscicos
-lsciscicos_blocks
-lsciscinotes
-lscishell
-lscisignal_processing
-lscisound
-lscisparse
-lscispecial_functions
-lscispreadsheet
-lscistatistics
-lscistring
-lscisundials
-lscisymbolic
-lscitclsci
-lscitime
-lsciui_data
-lsciumfpack
-lsciwindows_tools
-lscixcos

```

What shell are you using, can you show me what you get for a list if you dont exclude lib?

Also just some observations:

1. I wouldnt mix /usr/ and /usr/local paths when compiling/linking unless you are 100% certain you are using the same exact version in the system and manually compiled one. So if you want to compile against /usr/local I wouldnt use pkg-config but takes its output and update the paths accordingly to point to /usr/local (not sure if it will do that by itself based on environment variables).

2. The documentation said that the paths for the manually compiled version will probably be different than the binary version when linking so you may be missing an additional link directory. Can you past a directory listing for /usr/local/lib/scilab or compare its directory structure to what is recommended for source tree LD_LIBRARY_PATH in the link I pasted above.

3. Have you modified your shell environment variables at all (in particular those that deal with compiling/linking)?

---

### Post by melaine.gautier on 2013-12-20
Ok I found why I don't have the same result than you with the command 
"ls /usr/lib/scilab/ | sed 's/^lib/-l/g' | sed "s/\.so.*$//g" | sort | uniq | grep -v disable" it was because of option in my .bashrc ... now that I rename it's changing correctly the lib* 
I also removed the compiled version to only keep the one proposed by ubuntu package.

And then I managed to compile!! Thank a lot, your wonderful!!!

I need to look what's wrong in my bashrc and add all the libraries automaticaly with CMake but I know now that it's only a problem in my project and in my configuration. It's far better :-)

---

### Post by melaine.gautier on 2013-12-20
For the problem with the ls, it seems to come from a problem with the option --color (in my .bashrc I created the alias ls="ls --color") without this alias it's working perfectly

---

### Post by ju2wheels on 2013-12-20
Use absolute path /bin/ls I think should avoid triggering the alias so you can leave it in. Oddly though I have the same alias on my box although color is set to auto, see if that helps:

alias ls='ls --color=auto'

---

