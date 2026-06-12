---
title: "omnetpp 3.3 installation error (ubuntu 10.04)"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by mhmdmahdi on 2013-10-23
hello all, i'm trying to install omnet 3.3 on my ubuntu 10.04..
i need omnet 3.3 version because i already have the specific module to use for my research..

anyway, i had a problem while i  enter the "make" command to finish the installation..
belows are the errors shown up:

> mhmdmahdi@mhmdmahdi-desktop:~/omnetpp-3.3$ make
cd /home/mhmdmahdi/omnetpp-3.3/src/utils &&  make
make[1]: Entering directory `/home/mhmdmahdi/omnetpp-3.3/src/utils'
chmod +x opp_makemake opp_test opp_makedep opp_neddoc splitvec
cp opp_makemake /home/mhmdmahdi/omnetpp-3.3/bin
cp opp_test /home/mhmdmahdi/omnetpp-3.3/bin
cp opp_makedep /home/mhmdmahdi/omnetpp-3.3/bin
cp opp_neddoc /home/mhmdmahdi/omnetpp-3.3/bin
cp splitvec /home/mhmdmahdi/omnetpp-3.3/bin
cp neddoc.xsl /home/mhmdmahdi/omnetpp-3.3/bin
cp neddocproc.pl /home/mhmdmahdi/omnetpp-3.3/bin
../utils/install-prog seedtool /home/mhmdmahdi/omnetpp-3.3/bin
# next line is for samples/rundemo
echo wish >/home/mhmdmahdi/.wishname
make[1]: Leaving directory `/home/mhmdmahdi/omnetpp-3.3/src/utils'
cd /home/mhmdmahdi/omnetpp-3.3/src/nedxml && make
make[1]: Entering directory `/home/mhmdmahdi/omnetpp-3.3/src/nedxml'
g++ -c  -O2 -DNDEBUG=1   -DWITH_PARSIM -DWITH_NETBUILDER -I/usr/include/libxml2 -I/home/mhmdmahdi/omnetpp-3.3/include -I. -DBUILDING_NEDXML -o cppexprgenerator.o cppexprgenerator.cc
In file included from cppexprgenerator.cc:23:
nedcompiler.h: In member function ‘bool ltstr::operator()(const char*, const char*) const’:
nedcompiler.h:31: error: ‘strcmp’ was not declared in this scope
cppexprgenerator.cc: In function ‘bool isParameterConst(NEDElement*, const char*)’:
cppexprgenerator.cc:72: error: ‘strstr’ was not declared in this scope
cppexprgenerator.cc: In function ‘bool isIndexOp(NEDElement*)’:
cppexprgenerator.cc:77: error: ‘strcmp’ was not declared in this scope
cppexprgenerator.cc: In function ‘bool isSizeofOp(NEDElement*)’:
cppexprgenerator.cc:82: error: ‘strcmp’ was not declared in this scope
cppexprgenerator.cc: In member function ‘bool CppExpressionGenerator::needsExpressionClass(ExpressionNode*, NEDElement*)’:
cppexprgenerator.cc:188: error: ‘strcmp’ was not declared in this scope
cppexprgenerator.cc:190: error: ‘strcmp’ was not declared in this scope
cppexprgenerator.cc:192: error: ‘strcmp’ was not declared in this scope
cppexprgenerator.cc:194: error: ‘strcmp’ was not declared in this scope
cppexprgenerator.cc: In member function ‘void CppExpressionGenerator::doOperator(OperatorNode*, const char*, int)’:
cppexprgenerator.cc:448: error: ‘strcmp’ was not declared in this scope
cppexprgenerator.cc:458: error: ‘strcmp’ was not declared in this scope
cppexprgenerator.cc: In member function ‘void CppExpressionGenerator::doFunction(FunctionNode*, const char*, int)’:
cppexprgenerator.cc:514: error: ‘strcmp’ was not declared in this scope
make[1]: *** [cppexprgenerator.o] Error 1
make[1]: Leaving directory `/home/mhmdmahdi/omnetpp-3.3/src/nedxml'
make: *** [nedxml] Error 2
mhmdmahdi@mhmdmahdi-desktop:~/omnetpp-3.3$

really need help to figure this out :(
thanks for helping..

---

### Post by mörgæs on 2013-10-23
Hi, welcome to the fora.

10.04 is out of support and almost all users here have installed 12.04 or something newer.

Can you install Omnetpp in a later Buntu release?

---

