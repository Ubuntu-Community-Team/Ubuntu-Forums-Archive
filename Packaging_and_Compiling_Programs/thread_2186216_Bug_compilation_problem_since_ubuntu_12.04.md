---
title: "Bug compilation problem since ubuntu 12.04"
date: 2013-11-06
forum: Packaging and Compiling Programs
---

### Post by melaine.gautier on 2013-11-06
Hello,

I'm working on a project with call scilab for some dependancies but since I update my computer at ubuntu 12.04 (and now 13.10), I can't compile my project anymore and I need to use fedora or worst windows to work!!!!

I have a linking problem (but it was compiling before and there is no missing libraries)  - if you want I can share a short example program to reproduce this bug.

Here are the error display line :
```

 --$ make
[ 66%] Built target testLib
Linking CXX executable testScilab
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « com_ »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « callFunctionFromGateway »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « createNamedMatrixOfString »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « getNamedVarType »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « clearInternalLastError »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « checklhs_ »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « freeArrayOfString »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « intersci_ »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « setScilabMode »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « inisci_ »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « checkrhs_ »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « readNamedMatrixOfDouble »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « scirun_ »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « sciHasFigures »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « putlhsvar_ »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « getNamedVarDimension »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « setSCIpath »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « getScilabMode »
../lib/libtestLib.so.1.0: référence indéfinie vers « pvApiCtx »
../lib/libtestLib.so.1.0: référence indéfinie vers « isNamedDoubleType »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « getInternalLastErrorMessage »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « getInternalLastErrorValue »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « createvarfromptr_ »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « ExitScilab »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « settmpdir_ »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « InitializeLaunchScilabSignal »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « ReleaseLaunchScilabSignal »
../lib/libtestLib.so.1.0: référence indéfinie vers « getNamedScalarDouble »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « isdir »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « TerminateCorePart2 »
/usr/lib/scilab/libscicall_scilab.so: référence indéfinie vers « printError »
collect2: error: ld returned 1 exit status
make[2]: *** [bin/testScilab] Erreur 1
make[1]: *** [bin/CMakeFiles/testScilab.dir/all] Erreur 2
make: *** [all] Erreur 2

```

I also tried to compile scilab locally but then I have different errors but still linking errors : 
```

/usr/bin/g++   -Wall -Wextra -lpthread -ldl -m64 -lmpi_cxx  -fno-stack-protector -O3 -DNDEBUG     CMakeFiles/odinSimDevice.dir/main-sim.cpp.o  CMakeFiles/odinSimDevice.dir/simulator.cpp.o  -o ../../bin/odinSimDevice  -rdynamic -L/usr/local/lib/scilab -L/usr/local/../lib/scilab  -L/usr/local/modules/.libs -L/usr/local/modules/api_scilab/.libs  -L/usr/local/bin -lomniORB4 -lomnithread -lomniDynamic4  /usr/local/lib/scilab/libscilab.so  /usr/local/lib/scilab/libscicall_scilab.so  /usr/local/lib/scilab/libscilab-cli.so ../../lib/libodinStubs.so.5.0  ../../lib/libodinCom.so.5.0 ../../lib/libodinScilab.so.5.0  ../../lib/libodinDeviceLayersCore.so.5.0 ../../lib/libodinMath.so.5.0  ../../lib/libodinCom.so.5.0 ../../lib/libodinStubs.so.5.0 -lQtGui  -lQtXml -lQtCore -ldl  -Wl,-rpath,/usr/local/lib/scilab:/usr/local/../lib/scilab:/usr/local/modules/.libs:/usr/local/modules/api_scilab/.libs:/usr/local/bin:/home/melaine/INRIA/odin/build2/lib:  
/usr/local/lib/scilab/libscihdf5.so.5: undefined reference to `ompi_mpi_cxx_op_intercept'
/usr/local/lib/scilab/libscihdf5.so.5: undefined reference to `MPI::Datatype::Free()'
/usr/local/lib/scilab/libscihdf5.so.5: undefined reference to `MPI::Comm::Comm()'
/usr/local/lib/scilab/libscihdf5.so.5: undefined reference to `MPI::Win::Free()'

```

If anyone could help me, I'll be really greateful!!!
Melaine

---

### Post by spjackson on 2013-11-06
This looks like it's caused by the change to the default behaviour of ld a couple of years ago. See for example [URL="http://ubuntuforums.org/showthread.php?t=1859400"]http://ubuntuforums.org/showthread.php?t=1859400
[/URL]Libraries need to be listed after modules/libraries that call them, or use the --no-as-needed link flag.

---

### Post by melaine.gautier on 2013-11-07
It's working!!!!

Thank a lot for this information.

Now I need to find how to not need to add the line "-Wl,--no-as-needed" in my CXX_FLAGS of my CMake project.

But I can now come back to linux and ubuntu for working!!! What a great news :D

Thanks again

Mélaine

---

