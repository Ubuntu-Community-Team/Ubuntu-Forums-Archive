---
title: "ARToolKit can't run tests"
date: 2011-02-18
forum: Packaging and Compiling Programs
---

### Post by Juzzz on 2011-02-18
Hello all

I want to create a program with augmented reality and found that ARToolKit is a good start.

The problem is, is that i can't get it running.

i runned the ./Configure and make makefile. But when i want to run the simple in examples i get some 'cannot find' errors.

packages i installed:
- freeglut3-dev
- xorg-dev

error:
```

x@x:~/Programs/ARToolKit/examples/simple$ make
cc -o ../../bin/simpleTest simpleTest.o  -L/usr/X11R6/lib -L../../lib -lARgsub -lARvideo -lAR -lglut -lGLU -lGL -lXi -lXmu -lX11 -lm
/usr/bin/ld: cannot find -lARgsub
/usr/bin/ld: cannot find -lARvideo
/usr/bin/ld: cannot find -lAR
collect2: ld returned 1 exit status
make: *** [../../bin/simpleTest] Error 1

```

I try to search it but can't really find it.

i found out that i maybe need 'openvrml' to run it but i can't install it because of the following error:

```

x@x:~/Programs/AR/openvrml-0.18.6$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking how to run the C++ preprocessor... g++ -E
checking for gcj... no
checking dependency style of gcj... none
checking dependency style of gcj... (cached) none
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj static flag -static works... no
checking if gcj supports -c -o file.o... no
checking if gcj supports -c -o file.o... (cached) no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.18.0... yes
checking for gcj... no
checking for javac... no
checking for gcjh... no
checking for javah... no
checking for jar... no
checking for doxygen... no
checking for Rez... no
checking if the compiler supports the gcc visibility attribute... yes
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking ltdl.h usability... no
checking ltdl.h presence... no
checking for ltdl.h... no
configure: error: in `/home/x/Programs/AR/openvrml-0.18.6':
configure: error: ltdl.h not found
See `config.log' for more details.

```
 

I hope i gave enough information.

---

### Post by SevenMachines on 2011-02-19
Hi, there seems to be no problem building it here (note examples are built by default and but in bin/) Can you post your configure/make output for ARToolKit, i'm guessing somethings wrong there. 
Note also you dont need openvrml for the examples but its libltdl-dev you're missing for that

---

### Post by Juzzz on 2011-02-19
> **SevenMachines said:**
> Hi, there seems to be no problem building it here (note examples are built by default and but in bin/) Can you post your configure/make output for ARToolKit, i'm guessing somethings wrong there. 
Note also you dont need openvrml for the examples but its libltdl-dev you're missing for that

I first tried to install the 'libltdl-dev' package and tried to run the examples but no success.

new ./Configure

```

x@x:~/Programs/AR/ARToolKit$ ./Configure
Select a video capture driver.
  1: Video4Linux
  2: Video4Linux+JPEG Decompression (EyeToy)
  3: Digital Video Camcoder through IEEE 1394 (DV Format)
  4: Digital Video Camera through IEEE 1394 (VGA NONCOMPRESSED Image Format)
  5: GStreamer Media Framework
Enter : 2

Color conversion should use x86 assembly (not working for 64bit)?
Enter : y
Do you want to create debug symbols? (y or n)
Enter : y
Build gsub libraries with texture rectangle support? (y or n)
GL_NV_texture_rectangle is supported on most NVidia graphics cards
and on ATi Radeon and better graphics cards
Enter : y
  create ./Makefile
  create lib/SRC/Makefile
  create lib/SRC/AR/Makefile
  create lib/SRC/ARMulti/Makefile
  create lib/SRC/Gl/Makefile
  create lib/SRC/VideoLinux1394Cam/Makefile
  create lib/SRC/VideoLinuxDV/Makefile
  create lib/SRC/VideoLinuxV4L/Makefile
  create lib/SRC/VideoSGI/Makefile
  create lib/SRC/VideoMacOSX/Makefile
  create lib/SRC/VideoGStreamer/Makefile
  create lib/SRC/ARvrml/Makefile
  create util/Makefile
  create util/calib_camera2/Makefile
  create util/calib_cparam/Makefile
  create util/calib_distortion/Makefile
  create util/mk_patt/Makefile
  create util/graphicsTest/Makefile
  create util/videoTest/Makefile
  create examples/Makefile
  create examples/collide/Makefile
  create examples/exview/Makefile
  create examples/loadMultiple/Makefile
  create examples/modeTest/Makefile
  create examples/multi/Makefile
  create examples/optical/Makefile
  create examples/paddle/Makefile
  create examples/paddleDemo/Makefile
  create examples/paddleInteraction/Makefile
  create examples/range/Makefile
  create examples/relation/Makefile
  create examples/simple/Makefile
  create examples/simple2/Makefile
  create examples/simpleLite/Makefile
  create examples/twoView/Makefile
  create examples/simpleVRML/Makefile
  create include/AR/config.h
Done.

```

make command:

```

x@x:~/Programs/AR/ARToolKit$ make
(cd lib/SRC;    make -f Makefile)
make[1]: Entering directory `/home/x/Programs/AR/ARToolKit/lib/SRC'
(cd AR;         make -f Makefile)
make[2]: Entering directory `/home/x/Programs/AR/ARToolKit/lib/SRC/AR'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAlloc.c
ar rs ../../libAR.a mAlloc.o
ar: creating ../../libAR.a
rm -f mAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mFree.c
ar rs ../../libAR.a mFree.o
rm -f mFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocDup.c
ar rs ../../libAR.a mAllocDup.o
rm -f mAllocDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mDup.c
ar rs ../../libAR.a mDup.o
rm -f mDup.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocTrans.c
ar rs ../../libAR.a mAllocTrans.o
rm -f mAllocTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mTrans.c
ar rs ../../libAR.a mTrans.o
rm -f mTrans.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocMul.c
ar rs ../../libAR.a mAllocMul.o
rm -f mAllocMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mMul.c
ar rs ../../libAR.a mMul.o
rm -f mMul.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocInv.c
ar rs ../../libAR.a mAllocInv.o
rm -f mAllocInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mInv.c
ar rs ../../libAR.a mInv.o
rm -f mInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mSelfInv.c
ar rs ../../libAR.a mSelfInv.o
rm -f mSelfInv.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mAllocUnit.c
ar rs ../../libAR.a mAllocUnit.o
rm -f mAllocUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mUnit.c
ar rs ../../libAR.a mUnit.o
rm -f mUnit.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mDisp.c
ar rs ../../libAR.a mDisp.o
rm -f mDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mDet.c
ar rs ../../libAR.a mDet.o
rm -f mDet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include mPCA.c
ar rs ../../libAR.a mPCA.o
rm -f mPCA.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vAlloc.c
ar rs ../../libAR.a vAlloc.o
rm -f vAlloc.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vDisp.c
ar rs ../../libAR.a vDisp.o
rm -f vDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vFree.c
ar rs ../../libAR.a vFree.o
rm -f vFree.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vHouse.c
ar rs ../../libAR.a vHouse.o
rm -f vHouse.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vInnerP.c
ar rs ../../libAR.a vInnerP.o
rm -f vInnerP.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include vTridiag.c
ar rs ../../libAR.a vTridiag.o
rm -f vTridiag.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramGet.c
ar rs ../../libAR.a paramGet.o
rm -f paramGet.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramDecomp.c
ar rs ../../libAR.a paramDecomp.o
rm -f paramDecomp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramDistortion.c
ar rs ../../libAR.a paramDistortion.o
rm -f paramDistortion.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramChangeSize.c
ar rs ../../libAR.a paramChangeSize.o
rm -f paramChangeSize.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramFile.c
ar rs ../../libAR.a paramFile.o
rm -f paramFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include paramDisp.c
ar rs ../../libAR.a paramDisp.o
rm -f paramDisp.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arDetectMarker.c
ar rs ../../libAR.a arDetectMarker.o
rm -f arDetectMarker.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetTransMat.c
ar rs ../../libAR.a arGetTransMat.o
rm -f arGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetTransMat2.c
ar rs ../../libAR.a arGetTransMat2.o
rm -f arGetTransMat2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetTransMat3.c
ar rs ../../libAR.a arGetTransMat3.o
rm -f arGetTransMat3.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetTransMatCont.c
ar rs ../../libAR.a arGetTransMatCont.o
rm -f arGetTransMatCont.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arLabeling.c
ar rs ../../libAR.a arLabeling.o
rm -f arLabeling.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arDetectMarker2.c
ar rs ../../libAR.a arDetectMarker2.o
rm -f arDetectMarker2.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetMarkerInfo.c
ar rs ../../libAR.a arGetMarkerInfo.o
rm -f arGetMarkerInfo.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arGetCode.c
ar rs ../../libAR.a arGetCode.o
rm -f arGetCode.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arUtil.c
arUtil.c: In function ‘arGetVersion’:
arUtil.c:46: warning: incompatible implicit declaration of built-in function ‘exit’
ar rs ../../libAR.a arUtil.o
rm -f arUtil.o
make[2]: Leaving directory `/home/x/Programs/AR/ARToolKit/lib/SRC/AR'
(cd ARMulti;    make -f Makefile)
make[2]: Entering directory `/home/x/Programs/AR/ARToolKit/lib/SRC/ARMulti'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arMultiReadConfigFile.c
ar rs ../../libARMulti.a arMultiReadConfigFile.o
ar: creating ../../libARMulti.a
rm -f arMultiReadConfigFile.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arMultiGetTransMat.c
ar rs ../../libARMulti.a arMultiGetTransMat.o
rm -f arMultiGetTransMat.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include arMultiActivate.c
ar rs ../../libARMulti.a arMultiActivate.o
rm -f arMultiActivate.o
make[2]: Leaving directory `/home/x/Programs/AR/ARToolKit/lib/SRC/ARMulti'
(cd Gl;         make -f Makefile)
make[2]: Entering directory `/home/x/Programs/AR/ARToolKit/lib/SRC/Gl'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include gsub.c
ar rs ../../libARgsub.a gsub.o
ar: creating ../../libARgsub.a
rm -f gsub.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include gsubUtil.c
ar rs ../../libARgsubUtil.a gsubUtil.o
ar: creating ../../libARgsubUtil.a
rm -f gsubUtil.o
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include gsub_lite.c
gsub_lite.c:102: warning: "GL_TEXTURE_RECTANGLE" redefined
/usr/include/GL/glext.h:755: note: this is the location of the previous definition
gsub_lite.c:103: warning: "GL_PROXY_TEXTURE_RECTANGLE" redefined
/usr/include/GL/glext.h:757: note: this is the location of the previous definition
gsub_lite.c:104: warning: "GL_MAX_RECTANGLE_TEXTURE_SIZE" redefined
/usr/include/GL/glext.h:758: note: this is the location of the previous definition
gsub_lite.c: In function ‘arglCameraFrustum’:
gsub_lite.c:659: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
../../../include/AR/param.h:123: note: expected ‘double (*)[4]’ but argument is of type ‘const double (*)[4]’
gsub_lite.c: In function ‘arglCameraFrustumRH’:
gsub_lite.c:718: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
../../../include/AR/param.h:123: note: expected ‘double (*)[4]’ but argument is of type ‘const double (*)[4]’
ar rs ../../libARgsub_lite.a gsub_lite.o
ar: creating ../../libARgsub_lite.a
rm -f gsub_lite.o
make[2]: Leaving directory `/home/x/Programs/AR/ARToolKit/lib/SRC/Gl'
(cd VideoLinuxV4L; make -f Makefile)
make[2]: Entering directory `/home/x/Programs/AR/ARToolKit/lib/SRC/VideoLinuxV4L'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include ccvt_i386.S
ccvt_i386.S:32: fatal error: linux/linkage.h: No such file or directory
compilation terminated.
make[2]: *** [../../libARvideo.a(ccvt_i386.o)] Error 1
make[2]: Leaving directory `/home/x/Programs/AR/ARToolKit/lib/SRC/VideoLinuxV4L'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/x/Programs/AR/ARToolKit/lib/SRC'
make: *** [all] Error 2

```

---

### Post by SevenMachines on 2011-02-19
You'd need to install the linux headers package for your kernel to get past that error. But, at least here, there are more errors. I'm guessing linux/videodev.h is deprecated and the code would need to be updated. It looks like ARToolkit hasnt had a new release in a few years, i havent looked for svn activity to see it theres something newer to try yet.
As for getting something compiled...
Try the gstreamer option, 
5: GStreamer Media Framework
that worked for me, as did 
3: Digital Video Camcoder through IEEE 1394

---

### Post by Juzzz on 2011-02-19
> **SevenMachines said:**
> You'd need to install the linux headers package for your kernel to get past that error. But, at least here, there are more errors. I'm guessing linux/videodev.h is deprecated and the code would need to be updated. It looks like ARToolkit hasnt had a new release in a few years, i havent looked for svn activity to see it theres something newer to try yet.
As for getting something compiled...
Try the gstreamer option, 
5: GStreamer Media Framework
that worked for me, as did 
3: Digital Video Camcoder through IEEE 1394

If its really outdated maybe you know a better "toolkit" for Augmented Reality in c++?
When i searched on Google i thought that ARToolKit was a good one.

The main goal is that i use AR with 3d models (openGL).

---

### Post by SevenMachines on 2011-02-19
You'll know a lot more about which AR libraries are good ones than i do to be honest. Its just that artoolkit's last significant activity seems to be 2007, which is a long time in linux development terms. It might not take too much work to work it into newer kernel versions though. 
As i've mentioned, artoolkit gstreamer works mostly here, some examples segfault, some work, but if its not active then it might not be the library you're looking for. I'd always advise looking at the commits to svn or other vcs to see how 'alive' the project is when you're looking for one though. A good community with active forums and such is always something to look for too

---

### Post by jiapei100 on 2011-04-08
Hi, I can build ATToolkit with option 5: GStreamer Media Framework as well. But I'm not sure whether my testing is correct or not?
If you 
> 	cd {ARToolKit}/bin
	./simpleTest
, what is the result? Should there be some pictures captured by the webcam? Well, what I can obtain is just as shown in the picture
[IMG]http://www.visionopen.com/artoolkitsimpletest.png[/IMG]

Sorry, since I'm not quite familiar with ARToolkit, what should be displayed by this simpleTest is not clear. But, I'm expecting when testing by ./simpleTest, the camera should start capturing and show something on the screen, am I correct?

Cheers
JIA




> **SevenMachines said:**
> You'd need to install the linux headers package for your kernel to get past that error. But, at least here, there are more errors. I'm guessing linux/videodev.h is deprecated and the code would need to be updated. It looks like ARToolkit hasnt had a new release in a few years, i havent looked for svn activity to see it theres something newer to try yet.
As for getting something compiled...
Try the gstreamer option, 
5: GStreamer Media Framework
that worked for me, as did 
3: Digital Video Camcoder through IEEE 1394

---

### Post by SevenMachines on 2011-04-09
> **jiapei100 said:**
> Hi, I can build ATToolkit with option 5: GStreamer Media Framework as well. But I'm not sure whether my testing is correct or not?
Sorry, i'm only replying to let you know i'm not ignoring you! No ARToolKit choices work for me on ubuntu natty so i can't help you at all with this. The ARToolKit release is 4 years old now, and thats a lifetime in linux development terms. Although you could try using older ubuntu releases, or windows xp, perhaps on virtualbox to check it out, to me, no changes in 4 years means its effectively discontinued (although they may still be working on commercial versions). [FONT=Arial, Helvetica, sans-serif][SIZE=2]

Augmented Reality seems to be the 'next big thing' so i think quite a few open source libraries disappeared to become commercial. Hopefully someone can recommend a good free software alternative but its not my area[/SIZE][/FONT]

---

### Post by jiapei100 on 2011-04-09
Hi, SevenMachines:

Can you please recommend some good open sources here. It seems you are pretty familiar with this area -- Augmented Reality. I'd love to follow your suggestions.

Thank you ):P

Best Regards
JIA


> **SevenMachines said:**
> Sorry, i'm only replying to let you know i'm not ignoring you! No ARToolKit choices work for me on ubuntu natty so i can't help you at all with this. The ARToolKit release is 4 years old now, and thats a lifetime in linux development terms. Although you could try using older ubuntu releases, or windows xp, perhaps on virtualbox to check it out, to me, no changes in 4 years means its effectively discontinued (although they may still be working on commercial versions). [FONT=Arial, Helvetica, sans-serif][SIZE=2]

Augmented Reality seems to be the 'next big thing' so i think quite a few open source libraries disappeared to become commercial. Hopefully someone can recommend a good free software alternative but its not my area[/SIZE][/FONT]

---

### Post by SevenMachines on 2011-04-09
Sorry, i know absolutely nothing about augmented reality software or i would try and recommend something. If i hear of anything though i'll post it here

---

### Post by ipe_iv on 2011-07-12
Hi,

I am trying to utilize ARToolkit in Ubuntu 11.04 Desktop and using #5. GStreamer during the ./Configure stage,,,,
but during make... this is the error:

make[2]: Leaving directory `/home/ipe/Downloads/ARToolKit/lib/SRC/Gl'
(cd VideoGStreamer; make -f Makefile)
make[2]: Entering directory `/home/ipe/Downloads/ARToolKit/lib/SRC/VideoGStreamer'
cc -c -O -I/usr/X11R6/include -g -I../../../include video.c
video.c:16:18: fatal error: glib.h: No such file or directory
compilation terminated.
make[2]: *** [../../libARvideo.a(video.o)] Error 1
make[2]: Leaving directory `/home/ipe/Downloads/ARToolKit/lib/SRC/VideoGStreamer'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ipe/Downloads/ARToolKit/lib/SRC'
make: *** [all] Error 2

I am lost as to why it is not compiling :(...

---

### Post by Gwaeren on 2011-07-13
Hi

What configuration are you using? I got that error when choosing video4linux but with gstreamer it compiles without errors.

Hope it works!

---

### Post by ipe_iv on 2011-07-13
I am running Ubuntu via VMPlayer with Win7 as host....
i tried again via clean install from an Ubuntu Distro ISO (10.04.2 desktop)..

1. install Ubuntu
2. run updates to system
3. download 
[LIST]
[*][ARToolKit-2.72.1.tgz]("http://www.kameda-lab.org/_local/imagelab.tsukuba.ac.jp/ubuntu1004+opencv21/ARToolKitk/ARToolKit-2.72.1.tgz")
[*][artk-v4l2-2.72.1.20101003.patch]("http://www.kameda-lab.org/_local/imagelab.tsukuba.ac.jp/ubuntu1004+opencv21/ARToolKitk/artk-v4l2-2.72.1.20101003.patch")
[/LIST]
as indicated in [http://www.kameda-lab.org/_local/imagelab.tsukuba.ac.jp/ubuntu1004+opencv21/ARToolKitk/index-e.html](http://www.kameda-lab.org/_local/imagelab.tsukuba.ac.jp/ubuntu1004+opencv21/ARToolKitk/index-e.html) 
4. install libxmu-dev package --->>> sudo apt-get install ibxmu-dev
5. install freeglut3-dev package (for "missing glut.h error" when compiling)  --->>> sudo apt-get install freeglut3-dev
6. installed xorg-dev package (for "missing lxi error" when compiling)   --->>> sudo apt-get install xorg-dev
7. installed libjpeg-dev package (for "missing ljpeg error" when compiling) --->>> sudo apt-get install libjpeg-dev
8. untar the ARToolKit file -->> tar xzvf ARToolKit-2.72.1.tgz
9. run the patch file --->>> patch -p0 -d . < artk-v4l2-2.72.1.20101003.patch 

**** ARToolKit can now be compiled

--->>> $ ./Configure 
following choices for 1st selection works :
#3 Video4Linux2
#4 Digital Video Camcoder through IEEE 1394 (DV Format
#6 Digital Video Camcoder through IEEE 1394 (DV Format)
for 2nd (create debug symbols):
- we choose no
for 3rd (build gsub libraries....):
- we can choose Y or N since we have nvidia card , either way works..
--->>> $ make
- ARToolKit now compiled....

try running the tests now.... 
Good luck :)

**** i am just troubleshooting the camera parameters right now...

---

