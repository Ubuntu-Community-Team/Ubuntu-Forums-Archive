---
title: "linking to atlas/lapack/cblas"
date: 2007-10-06
forum: Programming Talk
---

### Post by spamalot on 2007-10-06
hi,

installed atlas and the test suite atlas3. however, i can't get to link to the libraries from eclipse. pls help.


make -k all
Building file: ../main.cpp
Invoking: GCC C++ Compiler
g++ -I/usr/local/include/boost_1_34_1
-I/usr/local/include/boost-bindings -O0 -g3 -Wall -c -fmessage-length=0
-MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.cpp"
Finished building: ../main.cpp

Building target: testing_numeric_bindings
Invoking: GCC C++ Linker
g++ -L/usr/lib -L/usr/lib/atlas -o"testing_numeric_bindings"  ./main.o
 -llapack -lf77blas -lcblas -latlas
/usr/bin/ld: cannot find -llapack
collect2: ld returned 1 exit status
make: *** [testing_numeric_bindings] Error 1
make: Target `all' not remade because of errors.
Build complete for project testing_numeric_bindings

alternatively,

make -k all
Building file: ../main.cpp
Invoking: GCC C++ Compiler
g++ -I/usr/local/include/boost_1_34_1
-I/usr/local/include/boost-bindings -O0 -g3 -Wall -c -fmessage-length=0
-MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.cpp"
Finished building: ../main.cpp

Building target: testing_numeric_bindings
Invoking: GCC C++ Linker
g++ -Wl,-rpath,/usr/lib,/usr/lib/atlas  -o"testing_numeric_bindings"
./main.o   -llapack -lf77blas -lcblas -latlas
/usr/bin/ld: /usr/lib/atlas: No such file: File format not recognized
collect2: ld returned 1 exit status
make: *** [testing_numeric_bindings] Error 1
make: Target `all' not remade because of errors.
Build complete for project testing_numeric_bindings

---

