---
title: "Problem with parallel program /usr/bin/ld: cannot find -lX11"
date: 2011-06-21
forum: Programming Talk
---

### Post by kelvin490 on 2011-06-21
I have a parallel program that requires "make" command to compile many source files. I use this "make all" command but get these messages:
 
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
gmake[1]: *** [../bin/paradis] Error 1

I cannot figure out what's wrong with my program and make files. Can anyone help me? Thank you.
 
More of the message is as follows:
 
Timer.o Topology.o TrapezoidIntegrator.o Util.o WriteArms.o WriteBinaryRestart.o WriteDensFlux.o WriteDensityField.o WriteFragments.o WritePoleFig.o WritePovray.o WriteProp.o WriteRestart.o WriteTSB.o WriteVelocity.o DisplayC.o display.o -o ../bin/paradis   -L/usr/lib64 -lX11 -lpthread   -lm
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
gmake[1]: *** [../bin/paradis] Error 1
gmake[1]: Leaving directory `/home/h0337502/parallel/src'
gmake[1]: Entering directory `/home/h0337502/parallel/src'
g++  CTableGen.o CorrectionTable.o FMSigma2.o FMSupport.o Heap.o MemCheck.o QueueOps.o Util.o -o ../bin/ctablegenp   -L/usr/lib64 -lX11 -lpthread   -lm
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
gmake[1]: *** [../bin/ctablegenp] Error 1
gmake[1]: Leaving directory `/home/h0337502/parallel/src'

---

### Post by dwhitney67 on 2011-06-21
You are missing the X11 library dependency on your system which is preventing you from building your application.  It is odd that the s/w you are building did not provide documentation to indicate its dependencies.  Did it have a "configure" script or a "README" file?

Anyhow, I believe the following is the package you need installed:
```

sudo apt-get install libx11-6

```

---

### Post by kelvin490 on 2011-06-21
> **dwhitney67 said:**
> You are missing the X11 library dependency on your system which is preventing you from building your application. It is odd that the s/w you are building did not provide documentation to indicate its dependencies. Did it have a "configure" script or a "README" file?
 
Anyhow, I believe the following is the package you need installed:
```

sudo apt-get install libx11-6

```
 
Thanks for reply.
I have the README file with only very few content:
 
 
    For general information on compiling, configuring, and running
    ParaDiS simulations, refer to the file:
        docs/ParaDiSInfo.txt

BTW, I am trying to run the program in a high performance multi-node computer which is a public facility in my university. Therefore, I am not allowed to install anything by myself. Does it mean the technical staff must install libx11-6 for me so that I can compile my program?

---

### Post by dwhitney67 on 2011-06-21
> **kelvin490 said:**
> Thanks for reply.
I have the README file with only very few content:
 
 
    For general information on compiling, configuring, and running
    ParaDiS simulations, refer to the file:
        docs/ParaDiSInfo.txt

BTW, I am trying to run the program in a high performance multi-node computer which is a public facility in my university. Therefore, I am not allowed to install anything by myself. Does it mean the technical staff must install libx11-6 for me so that I can compile my program?

It is possible that the library may already be installed, but is located in a different directory than your Makefile is specifying (currently /usr/lib64).  Consult with your System Administrator to see if the library (called libX11.so) is installed

If it not, then you have two choices:  1) persuade the SA to install it, or 2) download the source code for X11-R6 so that you can build the library yourself, and of course install it in a directory that you have access to.  Option 2 is not fun.

Back to the software you are attempting to build... did it not include a 'configure' script?

---

### Post by kelvin490 on 2011-06-21
> **dwhitney67 said:**
> It is possible that the library may already be installed, but is located in a different directory than your Makefile is specifying (currently /usr/lib64). Consult with your System Administrator to see if the library (called libX11.so) is installed
 
If it not, then you have two choices: 1) persuade the SA to install it, or 2) download the source code for X11-R6 so that you can build the library yourself, and of course install it in a directory that you have access to. Option 2 is not fun.
 
Back to the software you are attempting to build... did it not include a 'configure' script?
 
Thank you. It seems that I have to choose option 1. About the configure file, I can't find any file named "configure" in the folder of the whole set of program. Would it have other names? (e.g. makefile, makefile.setup, makefile.sys)

---

### Post by dwhitney67 on 2011-06-21
> **kelvin490 said:**
> Thank you. It seems that I have to choose option 1. About the configure file, I can't find any file named "configure" in the folder of the whole set of program. Would it have other names? (e.g. makefile, makefile.setup, makefile.sys)

I would consult with the document that you posted about earlier:
> 
For general information on **compiling**, **configuring**, and running
ParaDiS simulations, refer to the file:
docs/ParaDiSInfo.txt


---

