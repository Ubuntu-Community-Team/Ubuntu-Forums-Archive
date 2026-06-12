---
title: "How to install these programs?"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by paulemony on 2013-05-08
Can someone tell me how to install these downloaded programs?:


```
$:/usr/local/src/OpenCV-2.1.0$ ls3rdparty                  OpenCVFindPkgConfig.cmake
apps                      OpenCVFindTBB.cmake
autogen.sh                OpenCVInstallRequiredSystemLibraries.cmake
CMakeLists.txt            opencv.pc.cmake.in
cmake_uninstall.cmake.in  OpenCVPCHSupport.cmake
cvconfig.h.cmake          Package.cmake.in
data                      README
doc                       samples
include                   src
interfaces                tests
OpenCVConfig.cmake.in     utils
OpenCVFindLATEX.cmake
```



```
$:/usr/local/src/headtrack$ lsAUTHORS     autogen.sh~  COPYING  fgfs         headtrack.deb  Makefile  README
autogen.sh  ChangeLog    debian   headtrack.c  INSTALL        NEWS      TODO


]
```

The autogen.sh files I put there myself but they don't run:

```
#!/bin/bash

aclocal \
&& libtoolize -c -f -i \
&& automake --add-missing \
&& autoconf
``` 

I've installed autoconf:

```
$:/usr/local/src/headtrack$ whereis autoconf
autoconf: /usr/bin/autoconf /usr/share/autoconf /usr/share/man/man1/autoconf.1.gz
```
 
Documentation is either cryptic/out of date (headtrack) or over-engineered (OpenCV), just need to know what terminal commands to use, have tried make, cmake, makefile, ./config, and anything else I could think of, but always end up with error message of some sort (OpenCV needs to be installed first). 

Thx

---

### Post by steeldriver on 2013-05-08
Do you really need to install from source? Version 2.3 of the dev package is in the precise repos:

 ```
$ apt-cache policy libopencv-dev
libopencv-dev:
  Installed: (none)
  Candidate: 2.3.1-7
  Version table:
     2.3.1-7 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages

```

I've recently been playing with it for building gimp plugins - although I put it on a a couple of VMs so far (crunchbang and mint13) - I am happy to try it on my vanilla 12.04 Ubuntu box if it would help

---

### Post by ibjsb4 on 2013-05-08
Never did this and never will :) but this seems to be up to date.

[https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

---

### Post by steeldriver on 2013-05-08
... fwiw I just happened to try building the 2.4.5 version from the opencv git on my work's fedora box yesterday but I was thwarted by a broken python component at the install stage - I'd seriously suggest the OP installs their current repo's deb unless they absolutely *need* something newer

---

### Post by paulemony on 2013-05-08
The catch is that headtrack must have OpenCV-2.0.0 or 2.1.0, nothing else works, apparently.

---

### Post by steeldriver on 2013-05-08
OK, well then based on the instructions here --> [http://docs.opencv.org/doc/tutorials/introduction/linux_install/linux_install.html#linux-installation](http://docs.opencv.org/doc/tutorials/introduction/linux_install/linux_install.html#linux-installation)

it should proceed something like this (the directory name 'Build' is arbitrary but there seems to be a kind of convention to use it for cmake builds)

```
tar xjvf OpenCV-2.1.0.tar.bz2

cd OpenCV-2.1.0/
 
mkdir Build && cd Build

cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..

make

make install

```

[those are actually default values for those options - you can see all the options by running cmake interactively i.e. [FONT=courier new]cmake -i ..[/FONT] ]

HOWEVER for me on 12.04.02 the 'make' fails down at

```

.
.
.
/home/steeldriver/src/OpenCV-2.1.0/include/opencv/cxmat.hpp:387:5: error: ‘ptrdiff_t’ was not declared in this scope
/home/steeldriver/src/OpenCV-2.1.0/include/opencv/cxmat.hpp:387:5: note: suggested alternatives:
/usr/include/c++/4.6/i686-linux-gnu/./bits/c++config.h:156:28: note:   ‘std::ptrdiff_t’
/usr/include/c++/4.6/i686-linux-gnu/./bits/c++config.h:156:28: note:   ‘std::ptrdiff_t’
/home/steeldriver/src/OpenCV-2.1.0/include/opencv/cxmat.hpp:387:15: error: expected ‘;’ before ‘delta1’
.
.
.

```

In my experience, these kinds of compile errors related to system headers like /usr/include/c++/4.6/i686-linux-gnu/./bits/c++config.h usually mean you're going to have a pretty hard time compiling with the newer versions of gcc

** EDIT: the above error can be fixed by following instructions the bug report here --> [https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/791527](https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/791527)**

**However there are further build errors related to the ffmpeg components**

Sorry that's pretty much all I've got ... good luck and let us know how it goes

---

### Post by steeldriver on 2013-05-08
I've had a bit more of a play with this - it looks like the ffmpeg and  videodev components are pretty much broken (the dependent libs have  changed too much since the OpenCV 2.1.0 release) but apart from that and  1 distribution bug it will build on 12.04.2:

1. unpack the archive and create the build directory as above

```

tar xjvf OpenCV-2.1.0.tar.bz2

cd OpenCV-2.1.0/
 
mkdir Build && cd Build

```

2. fix the one actual bug that I mentioned previously - either open the cxcore.h file in a text editor and add the missing header or (from your Build directory)

```

steeldriver@lap-t61p:~/src/OpenCV-2.1.0/Build$ sed -i '/#include "cxtypes.h"/i#include <stddef.h>' ../include/opencv/cxcore.h

```

3. configure with Cmake using the following build options

```

steeldriver@lap-t61p:~/src/OpenCV-2.1.0/Build$ cmake [COLOR=#0000ff]-D OPENCV_EXTRA_C_FLAGS=-D__STDC_CONSTANT_MACROS -D WITH_FFMPEG=NO -D WITH_V4L=NO[/COLOR] ..

```

After that it *should* all build

```

steeldriver@lap-t61p:~/src/OpenCV-2.1.0/Build$ make

```

I haven't tried to 'make install' because I don't want to screw up my OpenCV2.3 installation

Hope this helps

---

### Post by paulemony on 2013-05-09
That seems to have done it, many thx, would never have worked that out in a million years! One odd thing though, OpenCV-2.1.0 doesn't show up as installed in Synaptic, though I'm not sure if it should.

Still need to install the main program "headtrack":

```
[COLOR=#000000][FONT=Ubuntu Mono]$:/usr/local/src/headtrack$ lsAUTHORS     autogen.sh~  COPYING  fgfs         headtrack.deb  Makefile  README
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]autogen.sh  ChangeLog    debian   headtrack.c  INSTALL        NEWS      TODO[/FONT][/COLOR]
```

INSTALL says 
> I. Instructions for headtrack:

0. To test headtrack type 'make' and run ./headtrack


1. Only if  you receive an error message about the missing cascade file:
   Copy the haarcascade_frontalface_alt.xml file from your OpenCV installation to
   "/usr/local/headtrack/haarcascade_frontalface_alt.xml"
   (Or change the path in the sourcecode according to your distribution)


2. Type 'make install' to compile the program headtrack and 
   install it to /usr/bin/headtrack

but 

```
$:/usr/local/src/headtrack$ make
gcc -msse -I/usr/include/X11 -W -msse2 -std=c99 -fomit-frame-pointer  -fno-strict-aliasing -m64 -mtune=amdfam10 -Wno-unused-parameter -Wno-unused-value -Wno-unused-function -W -Wall -O3 -I/usr/include/X11 `pkg-config --cflags --libs opencv x11 gtk+-2.0 gthread-2.0` -o headtrack headtrack.c
headtrack.c: In function ‘main’:
headtrack.c:105:7: warning: variable ‘new_transmitterthread’ set but not used [-Wunused-but-set-variable]
/usr/bin/ld: cannot open output file headtrack: Is a directory
collect2: ld returned 1 exit status
make: *** [headtrack64] Error 1



```

---

### Post by steeldriver on 2013-05-09
I think the *only* thing that can mean is that you have a subdirectory called 'headtrack' in the directory where you're trying to compile 'headtrack' - which is odd since it doesn't show up in your 'ls' output

For example if I compile and test a little hello.c example it works:

```
$ gcc -Wall -o hello hello.c
$
$ ./hello
Hello world!

```

but if I then delete the executable and create a dir in its place
```

$ rm hello; mkdir hello

```

then it won't let me recompile it
```
$ gcc -Wall -o hello hello.c
/usr/bin/ld: cannot open output file hello: Is a directory
collect2: ld returned 1 exit status
$
```

---

### Post by paulemony on 2013-05-09
Very strange, I did try [FONT=arial][COLOR=#000000]**mkdir Build && cd Build** in the main directory but **Build** is empty, however when I look now there is indeed a sub-directory **headtrack** (maybe it just "fell off" when I originally copied & pasted the list). I don't profess to understand your example but here's the complete list from the sub-directory:

[/COLOR][/FONT]```
$:/usr/local/src/headtrack/headtrack$ ls
DEBIAN  usr

$:/usr/local/src/headtrack/headtrack/DEBIAN$ ls
control

$:/usr/local/src/headtrack/headtrack/usr$ ls
bin  share

$:/usr/local/src/headtrack/headtrack/usr/bin$ ls
headtrack   (executable)

$:/usr/local/src/headtrack/headtrack/usr/share$ ls
headtrack  (empty folder)
[FONT=arial][COLOR=#000000]

[/COLOR][/FONT]
```[FONT=arial][COLOR=#000000]
[/COLOR][/FONT]

---

### Post by steeldriver on 2013-05-09
The 'mkdir Build && cd Build' commands ONLY related to the (Cmake-based) build of the OpenCV library - no need to do those for the actual headtrack build, as far as I can see from the INSTALL file 'headtrack' just requires a simple 'make' in the same directory as the headtrack.c file

```
$ cd /usr/local/src/headtrack
$ make
```

However it looks like something has tried to do a 'make install' but taken your current directory as the install root (instead of the real system root '/') so that it has created a whole 'root tree' in the current dir i.e. **./**usr, **./**usr/bin etc.

If you post the headtrack Makefile we can try to puzzle it out, or you can just remove the whole spurious tree from /usr/local/src/headtrack/headtrack down and try the 'make' command again

---

### Post by paulemony on 2013-05-09
Yes, /usr/local/src/headtrack/headtrack just duplicates /usr/local/src/headtrack/debian, which contains DEBIAN and usr folders.

Makefile:

> CFLAGS= -msse -I/usr/include/X11 -W -msse2 -std=c99 -fomit-frame-pointer 

headtrack64: headtrack.c
    gcc $(CFLAGS) -fno-strict-aliasing -m64 -mtune=amdfam10 -Wno-unused-parameter -Wno-unused-value -Wno-unused-function -W -Wall -O3 -I/usr/include/X11 `pkg-config --cflags --libs opencv x11 gtk+-2.0 gthread-2.0` -o headtrack headtrack.c


headtrack32: headtrack.c
    gcc -std=c99 -fno-strict-aliasing -Wno-unused-parameter -Wno-unused-value -Wno-unused-function -W -Wall -O2 -I/usr/include/X11 `pkg-config --cflags --libs opencv x11 gtk+-2.0 gthread-2.0` -m32 -o headtrack32 headtrack.c


deb64: headtrack64
    mkdir -p ./debian/usr/bin 
    mkdir -p ./debian/usr/share/headtrack
    cp headtrack ./debian/usr/bin/headtrack
    dpkg --build debian
    mv debian.deb headtrack.deb


deb32: headtrack32
    mkdir -p ./debian/usr/bin 
    mkdir -p ./debian/usr/share/headtrack
    cp headtrack32 ./debian/usr/bin/headtrack
    dpkg --build debian
    mv debian.deb headtrack.deb


installdeb: deb64
    sudo dpkg -i headtrack.deb
    sudo cp /usr/share/doc/opencv-doc/examples/haarcascades/haarcascades/haarcascade_frontalface_alt.xml.gz /usr/local/headtrack/haarcascade_frontalface_alt.xml.gz
    sudo gunzip /usr/local/headtrack/haarcascade_frontalface_alt.xml.gz


install: headtrack
    cp headtrack /usr/bin/headtrack


install-fgfiles:
    cp fgfs/FG_ROOT/gui/dialogs/headtracking.xml $(FG_ROOT)/gui/dialogs/headtracking.xml
    mv $(FG_ROOT)/gui/menubar.xml $(FG_ROOT)/gui/menubar.xml.orignal
    cp fgfs/FG_ROOT/gui/menubar.xml $(FG_ROOT)/gui/menubar.xml 
    cp fgfs/FG_ROOT/Protocol/headtrack.xml $(FG_ROOT)/Protocol/headtrack.xml
 
install-nasfile:
    cp fgfs/headtracking.nas $(HOME)/.fgfs/Nasal/headtracking.nas


uninstall: 
    rm -f /usr/bin/headtrack


clean: 
    rm -f ./headtrack
    rm -f ./headtrack.deb
    rm -f ./headtrack32
    rm -f ./debian/usr/bin/headtrack


run: 
    ./headtrack




---

### Post by paulemony on 2013-05-09
P.S. Deleted sub-directory & tried "make" again:

```
$:/usr/local/src/headtrack$ makegcc -msse -I/usr/include/X11 -W -msse2 -std=c99 -fomit-frame-pointer  -fno-strict-aliasing -m64 -mtune=amdfam10 -Wno-unused-parameter -Wno-unused-value -Wno-unused-function -W -Wall -O3 -I/usr/include/X11 `pkg-config --cflags --libs opencv x11 gtk+-2.0 gthread-2.0` -o headtrack headtrack.c
headtrack.c: In function ‘main’:
headtrack.c:105:7: warning: variable ‘new_transmitterthread’ set but not used [-Wunused-but-set-variable]
/tmp/cc7SSsHs.o: In function `main':
headtrack.c:(.text.startup+0x247): undefined reference to `cvLoad'
headtrack.c:(.text.startup+0x27a): undefined reference to `cvCreateImage'
headtrack.c:(.text.startup+0x29a): undefined reference to `cvCreateImage'
headtrack.c:(.text.startup+0x2ba): undefined reference to `cvCreateImage'
headtrack.c:(.text.startup+0x2de): undefined reference to `cvCreateImage'
headtrack.c:(.text.startup+0x2fe): undefined reference to `cvCreateImage'
headtrack.c:(.text.startup+0x318): undefined reference to `cvNamedWindow'
headtrack.c:(.text.startup+0x322): undefined reference to `cvGetWindowHandle'
headtrack.c:(.text.startup+0x32f): undefined reference to `g_type_check_instance_cast'
headtrack.c:(.text.startup+0x347): undefined reference to `g_signal_connect_data'
headtrack.c:(.text.startup+0x3b8): undefined reference to `cvCreateMat'
headtrack.c:(.text.startup+0x3d3): undefined reference to `cvCreateMat'
headtrack.c:(.text.startup+0x3e6): undefined reference to `cvSetZero'
headtrack.c:(.text.startup+0x3f2): undefined reference to `cvSetZero'
headtrack.c:(.text.startup+0x41d): undefined reference to `cv2DRotationMatrix'
headtrack.c:(.text.startup+0x448): undefined reference to `cv2DRotationMatrix'
headtrack.c:(.text.startup+0x44f): undefined reference to `cvCreateMemStorage'
headtrack.c:(.text.startup+0x46b): undefined reference to `cvCreateCameraCapture'
headtrack.c:(.text.startup+0x4a5): undefined reference to `cvQueryFrame'
headtrack.c:(.text.startup+0x4b9): undefined reference to `cvResize'
headtrack.c:(.text.startup+0x4d1): undefined reference to `cvCvtColor'
headtrack.c:(.text.startup+0x505): undefined reference to `cvHaarDetectObjects'
headtrack.c:(.text.startup+0x753): undefined reference to `atan'
headtrack.c:(.text.startup+0x79e): undefined reference to `atan'
headtrack.c:(.text.startup+0x80f): undefined reference to `cvGetSeqElem'
headtrack.c:(.text.startup+0x906): undefined reference to `cv2DRotationMatrix'
headtrack.c:(.text.startup+0x938): undefined reference to `cv2DRotationMatrix'
headtrack.c:(.text.startup+0xa14): undefined reference to `cvRectangle'
headtrack.c:(.text.startup+0xc28): undefined reference to `cvRectangle'
headtrack.c:(.text.startup+0xc3b): undefined reference to `cvFlip'
headtrack.c:(.text.startup+0xc53): undefined reference to `cvPyrDown'
headtrack.c:(.text.startup+0xc64): undefined reference to `cvShowImage'
headtrack.c:(.text.startup+0xc6e): undefined reference to `cvWaitKey'
headtrack.c:(.text.startup+0xc82): undefined reference to `cvReleaseMat'
headtrack.c:(.text.startup+0xc8e): undefined reference to `cvReleaseMat'
headtrack.c:(.text.startup+0xc9a): undefined reference to `cvReleaseHaarClassifierCascade'
headtrack.c:(.text.startup+0xca6): undefined reference to `cvReleaseCapture'
headtrack.c:(.text.startup+0xcb0): undefined reference to `cvDestroyWindow'
headtrack.c:(.text.startup+0xcbc): undefined reference to `cvReleaseMemStorage'
headtrack.c:(.text.startup+0xd98): undefined reference to `cvWarpAffine'
headtrack.c:(.text.startup+0xdcc): undefined reference to `cvHaarDetectObjects'
headtrack.c:(.text.startup+0xe4c): undefined reference to `cvWarpAffine'
headtrack.c:(.text.startup+0xe80): undefined reference to `cvHaarDetectObjects'
headtrack.c:(.text.startup+0xeae): undefined reference to `cvLoad'
headtrack.c:(.text.startup+0xece): undefined reference to `cvLoad'
collect2: ld returned 1 exit status
make: *** [headtrack64] Error 1



```

---

### Post by steeldriver on 2013-05-09
Well I don't see anything there that would have created those extra dirs - perhaps they were stubs that got left in the headtrack tarball (assuming you unpacked it from a tarball)?

Regardless, there doesn't appear to be anything of value in them so I still suggest removing the /usr/local/src/headtrack/headtrack directory which is blocking creation of the identically named headtrack executable file, and then running either

```
make headtrack32
```

```
make headtrack64
```

depending on your platform (if you just run 'make' with no target argument it looks like it will try to build the 64-bit version, since that's the default target in the Makefile)


EDIT: just seen you most recent post, that's all looking good except there's a library order issue - the current linker doesn't attempt to resolve references like that so you will need to modify the Makefile a little to get everything in the right order manually:

```

headtrack64: headtrack.c
gcc $(CFLAGS) -fno-strict-aliasing -m64 -mtune=amdfam10 -Wno-unused-parameter -Wno-unused-value -Wno-unused-function -W -Wall -O3 -I/usr/include/X11 **`pkg-config --cflags [COLOR=#ff0000]--libs[/COLOR] opencv x11 gtk+-2.0 gthread-2.0`** -o headtrack headtrack.c

```

to
```

headtrack64: headtrack.c
gcc $(CFLAGS) -fno-strict-aliasing -m64 -mtune=amdfam10 -Wno-unused-parameter -Wno-unused-value -Wno-unused-function -W -Wall -O3 -I/usr/include/X11 **`pkg-config --cflags opencv x11 gtk+-2.0 gthread-2.0`** -o headtrack headtrack.c **`pkg-config [COLOR=#ff0000]--libs[/COLOR] opencv x11 gtk+-2.0 gthread-2.0`**

```

i.e. split the 'cflags' and 'libs' parts of pkg-config and put the 'libs' part AFTER the headtrack.c file (same for the 32-bit target if you want to build that)

---

### Post by paulemony on 2013-05-09
OK, Makefile now:

> CFLAGS= -msse -I/usr/include/X11 -W -msse2 -std=c99 -fomit-frame-pointer 



headtrack64: headtrack.c
gcc $(CFLAGS) -fno-strict-aliasing -m64 -mtune=amdfam10 -Wno-unused-parameter -Wno-unused-value -Wno-unused-function -W -Wall -O3 -I/usr/include/X11 `pkg-config --cflags opencv x11 gtk+-2.0 gthread-2.0` -o headtrack headtrack.c `pkg-config --libs opencv x11 gtk+-2.0 gthread-2.0`


headtrack32: headtrack.c
    gcc -std=c99 -fno-strict-aliasing -Wno-unused-parameter -Wno-unused-value -Wno-unused-function -W -Wall -O2 -I/usr/include/X11 `pkg-config --cflags --libs opencv x11 gtk+-2.0 gthread-2.0` -m32 -o headtrack32 headtrack.c


deb64: headtrack64
    mkdir -p ./debian/usr/bin 
    mkdir -p ./debian/usr/share/headtrack
    cp headtrack ./debian/usr/bin/headtrack
    dpkg --build debian
    mv debian.deb headtrack.deb


deb32: headtrack32
    mkdir -p ./debian/usr/bin 
    mkdir -p ./debian/usr/share/headtrack
    cp headtrack32 ./debian/usr/bin/headtrack
    dpkg --build debian
    mv debian.deb headtrack.deb


installdeb: deb64
    sudo dpkg -i headtrack.deb
    sudo cp /usr/share/doc/opencv-doc/examples/haarcascades/haarcascades/haarcascade_frontalface_alt.xml.gz /usr/local/headtrack/haarcascade_frontalface_alt.xml.gz
    sudo gunzip /usr/local/headtrack/haarcascade_frontalface_alt.xml.gz


install: headtrack
    cp headtrack /usr/bin/headtrack


install-fgfiles:
    cp fgfs/FG_ROOT/gui/dialogs/headtracking.xml $(FG_ROOT)/gui/dialogs/headtracking.xml
    mv $(FG_ROOT)/gui/menubar.xml $(FG_ROOT)/gui/menubar.xml.orignal
    cp fgfs/FG_ROOT/gui/menubar.xml $(FG_ROOT)/gui/menubar.xml 
    cp fgfs/FG_ROOT/Protocol/headtrack.xml $(FG_ROOT)/Protocol/headtrack.xml
 
install-nasfile:
    cp fgfs/headtracking.nas $(HOME)/.fgfs/Nasal/headtracking.nas


uninstall: 
    rm -f /usr/bin/headtrack


clean: 
    rm -f ./headtrack
    rm -f ./headtrack.deb
    rm -f ./headtrack32
    rm -f ./debian/usr/bin/headtrack


run: 
    ./headtrack




However:

```
$:/usr/local/src/headtrack$ make headtrack64
make: Nothing to be done for `headtrack64'.


$:/usr/local/src/headtrack$ make headtrack
cc -msse -I/usr/include/X11 -W -msse2 -std=c99 -fomit-frame-pointer     headtrack.c   -o headtrack
headtrack.c:42:16: fatal error: cv.h: No such file or directory
compilation terminated.
make: *** [headtrack] Error 1


$:/usr/local/src/headtrack$ make
make: Nothing to be done for `headtrack64'.
```

---

### Post by steeldriver on 2013-05-09
Hi again

The Makefile seems like it needs some tidying up - there doesn't appear to be an actual 'headtrack' target, only the separate 'headtrack64' and 'headtrack32' targets. So when you try to 'make headtrack' it just guesses how to build it (or more precisely, it uses default rules for making an executable from a .c file) - which doesn't include any of the pkg-configs or other stuff (just the CFLAGS) - so it fails. And the 'clean' rules don't reflect the 32/64 bit distinction correctly. 

Since it's only a single .c file creating a single executable probably the easiest thing is to forget about 'make' altogether and just run the compiler directly e.g. gluing together (and rationalizing) all the options for the 64-bit build [I don't know if any of these options - except for the warnings (-Wxx) - are actually good to use BTW]

```

$ rm headtrack
$ rm *.o
$
$ CFLAGS="-msse -msse2 -std=c99 -fomit-frame-pointer -fno-strict-aliasing -m64 -mtune=amdfam10 -Wall -Wextra -O3 -I/usr/include/X11 `pkg-config --cflags opencv x11 gtk+-2.0 gthread-2.0`"
$ LIBS="`pkg-config --libs opencv x11 gtk+-2.0 gthread-2.0`"
$ 
$ gcc $CFLAGS -o headtrack  headtrack.c $LIBS

```

---

### Post by paulemony on 2013-05-10
Not sure I understand why the **rm **command, does the entire **headtrack **directory have to be removed?

Command doesn't work anyway:

```
$:/usr/local/src$ rm headtrack
rm: cannot remove `headtrack': Is a directory
```

I suppose I could just erase it with nautilus?

Another problem, dicovered that OpenCV-2.1.0 isn't installed after all even though it looked as if it was:

```
$:/usr/local/src/OpenCV-2.1.0/Build$ sudo make install[ 47%] Built target opencv_lapack
[ 48%] Built target flann
[ 51%] Built target zlib
[ 54%] Built target cxcore
[ 64%] Built target cv
[ 68%] Built target highgui
[ 70%] Built target ml
[ 83%] Built target cvaux
[ 84%] Built target cvhaartraining
[ 84%] Built target createsamples
[ 84%] Built target haartraining
[ 84%] Built target performance
[ 85%] Built target traincascade
[ 85%] Built target cxts
[ 96%] Built target cvtest
[ 99%] Built target cxcoretest
[100%] Built target mltest
[100%] Built target cvpy
Install the project...
-- Install configuration: "RELEASE"
-- Installing: /usr/local/share/opencv/OpenCVConfig.cmake
-- Installing: /usr/local/lib/pkgconfig/opencv.pc
-- Installing: /usr/local/lib/libcxcore.so.2.1.0
-- Up-to-date: /usr/local/lib/libcxcore.so.2.1
-- Up-to-date: /usr/local/lib/libcxcore.so
-- Installing: /usr/local/include/opencv/cxcore.h
-- Up-to-date: /usr/local/include/opencv/cxcore.hpp
-- Up-to-date: /usr/local/include/opencv/cxerror.h
-- Up-to-date: /usr/local/include/opencv/cxmat.hpp
-- Up-to-date: /usr/local/include/opencv/cxmisc.h
-- Up-to-date: /usr/local/include/opencv/cxoperations.hpp
-- Up-to-date: /usr/local/include/opencv/cxtypes.h
-- Up-to-date: /usr/local/include/opencv/cvver.h
-- Up-to-date: /usr/local/include/opencv/cvwimage.h
-- Up-to-date: /usr/local/include/opencv/cxflann.h
-- Up-to-date: /usr/local/include/opencv/cvinternal.h
-- Installing: /usr/local/lib/libcv.so.2.1.0
-- Up-to-date: /usr/local/lib/libcv.so.2.1
-- Up-to-date: /usr/local/lib/libcv.so
-- Removed runtime path from "/usr/local/lib/libcv.so.2.1.0"
-- Up-to-date: /usr/local/include/opencv/cv.h
-- Up-to-date: /usr/local/include/opencv/cv.hpp
-- Up-to-date: /usr/local/include/opencv/cvcompat.h
-- Up-to-date: /usr/local/include/opencv/cvtypes.h
-- Installing: /usr/local/lib/libcvaux.so.2.1.0
-- Up-to-date: /usr/local/lib/libcvaux.so.2.1
-- Up-to-date: /usr/local/lib/libcvaux.so
-- Removed runtime path from "/usr/local/lib/libcvaux.so.2.1.0"
-- Up-to-date: /usr/local/include/opencv/cvaux.h
-- Up-to-date: /usr/local/include/opencv/cvaux.hpp
-- Up-to-date: /usr/local/include/opencv/cvvidsurv.hpp
-- Installing: /usr/local/lib/libml.so.2.1.0
-- Up-to-date: /usr/local/lib/libml.so.2.1
-- Up-to-date: /usr/local/lib/libml.so
-- Removed runtime path from "/usr/local/lib/libml.so.2.1.0"
-- Up-to-date: /usr/local/include/opencv/ml.h
-- Installing: /usr/local/lib/libhighgui.so.2.1.0
-- Up-to-date: /usr/local/lib/libhighgui.so.2.1
-- Up-to-date: /usr/local/lib/libhighgui.so
-- Removed runtime path from "/usr/local/lib/libhighgui.so.2.1.0"
-- Up-to-date: /usr/local/include/opencv/highgui.h
-- Up-to-date: /usr/local/include/opencv/highgui.hpp
-- Installing: /usr/local/bin/opencv_haartraining
-- Removed runtime path from "/usr/local/bin/opencv_haartraining"
-- Installing: /usr/local/bin/opencv_createsamples
-- Removed runtime path from "/usr/local/bin/opencv_createsamples"
-- Installing: /usr/local/bin/opencv_performance
-- Removed runtime path from "/usr/local/bin/opencv_performance"
-- Installing: /usr/local/bin/opencv_traincascade
-- Removed runtime path from "/usr/local/bin/opencv_traincascade"
-- Up-to-date: /usr/local/share/opencv/doc/index.htm
-- Up-to-date: /usr/local/share/opencv/doc/ChangeLog.htm
-- Up-to-date: /usr/local/share/opencv/doc/haartraining.htm
-- Up-to-date: /usr/local/share/opencv/doc/CMakeLists.txt
-- Up-to-date: /usr/local/share/opencv/doc/license.txt
-- Up-to-date: /usr/local/share/opencv/doc/packaging.txt
-- Up-to-date: /usr/local/share/opencv/doc/README.txt
-- Up-to-date: /usr/local/share/opencv/doc/opencv.jpg
-- Up-to-date: /usr/local/share/opencv/doc/opencv-logo.png
-- Up-to-date: /usr/local/share/opencv/doc/opencv-logo2.png
-- Up-to-date: /usr/local/share/opencv/doc/opencv.pdf
-- Up-to-date: /usr/local/share/opencv/doc/pattern.pdf
-- Up-to-date: /usr/local/share/opencv/doc/papers/camshift.pdf
-- Up-to-date: /usr/local/share/opencv/doc/papers/algo_tracking.pdf
-- Up-to-date: /usr/local/share/opencv/doc/papers/avbpa99.ps
-- Up-to-date: /usr/local/share/opencv/doc/vidsurv/Blob_Tracking_Tests.doc
-- Up-to-date: /usr/local/share/opencv/doc/vidsurv/TestSeq.doc
-- Up-to-date: /usr/local/share/opencv/doc/vidsurv/Blob_Tracking_Modules.doc
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_frontalface_alt_tree.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_eye.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_mcs_eyepair_small.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_mcs_nose.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_mcs_mouth.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_mcs_righteye.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_lowerbody.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_mcs_upperbody.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_mcs_eyepair_big.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_mcs_lefteye.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_upperbody.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_eye_tree_eyeglasses.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_lefteye_2splits.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_frontalface_default.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_frontalface_alt.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_fullbody.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_profileface.xml
-- Up-to-date: /usr/local/share/opencv/haarcascades/haarcascade_righteye_2splits.xml
-- Up-to-date: /usr/local/share/opencv/lbpcascades/lbpcascade_frontalface.xml
-- Installing: /usr/local/lib/python2.7/site-packages/cv.so
$:/usr/local/src/OpenCV-2.1.0/Build$ dpkg -s opencv
Package `opencv' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```

In a bind here, if I'd known this was going to be such hard work I wouldn't have bothered (it really shouldn't be this complicated, surely?), but on the other hand having spent so much time on it reluctant to abandon it if the solution is just around the corner.

---

### Post by steeldriver on 2013-05-10
**NOOOO! I meant to execute the rm command INSIDE your /src/headtrack directory - to delete the most recent heatrack executable. Sorry if that wasn't clear.** 

I think you *will* be able to get headrack to build HOWEVER it's possible that it won't actually run without the OpenCV components that we had to exclude in order to get *that* to build.

I'll post back again shortly - just wanted to clear up the confusion about the rm command ASAP

---

### Post by steeldriver on 2013-05-10
OK here's a Makefile that should let you build headtrack from a (relative) local build of OpenCV-2.1.0 i.e. WITHOUT actually installing the old OpenCV libraries. It assumes that your local source tree looks like

```

$ tree -L 1
.
&#9500;&#9472;&#9472; headtrack
[COLOR=#a9a9a9]&#9500;&#9472;&#9472; nlopt[/COLOR]
&#9500;&#9472;&#9472; OpenCV-2.1.0
[COLOR=#a9a9a9]&#9492;&#9472;&#9472; optpp[/COLOR]

4 directories, 0 files

```

i.e. the top level headtrack and OpenCV-2.1.0 directories are untarred side-by-side. I got the headtrack distribution from [https://git.gitorious.org/headtrack/headtrack.git](https://git.gitorious.org/headtrack/headtrack.git) , I hope that's the one we're dealing with here (there do seem to be some other possibly newer OpenCV based headtrack projects out there).

```

CC = gcc

TRGT = headtrack

SRCS = headtrack.c

OBJS = $(SRCS:.c=.o)

INSTDIR = /usr/bin


CFLAGS := -std=c99 -Wall -Wextra -msse -msse2 \
    -fomit-frame-pointer -fno-strict-aliasing \
    -I/usr/include/X11 $(shell pkg-config --cflags gtk+-2.0 gthread-2.0)

# to find the regularly-installed OpenCV
#CFLAGS += $(shell pkg-config --cflags opencv) 
# to find local version of OpenCV
CFLAGS += -I../OpenCV-2.1.0/include/opencv

ARCH := $(shell uname -m)
ifeq ($(ARCH), x86_64)
  CFLAGS += -m64 -mtune=amdfam10 -O3
else
  CFLAGS += -m32 -O2
endif

# to find the regularly-installed OpenCV
#LPATH :=
# to find local version of OpenCV
LPATH := -L../OpenCV-2.1.0/Build/lib/

#LIBS := $(shell pkg-config --libs opencv gtk+-2.0 gthread-2.0)
LIBS := -lml -lcvaux -lhighgui -lcv  -lcxcore \
    $(shell pkg-config --libs gtk+-2.0 gthread-2.0)

$(TRGT): $(OBJS)
    $(CC) $(OBJS) $(LPATH) $(LIBS) -o $@


install: $(TRGT)
    cp $(TRGT) $(INSTALLDIR)/$(TRGT)

uninstall: 
    rm -f $(INSTALLDIR)/$(TRGT)


clean: 
    rm -f $(OBJS)

cleaner: clean
    rm -f $(TRGT)

cleanest: cleaner
    

```

It worked for me on my 32-bit laptop with 12.04.2; I also got it to build in a 64-bit crunchbang VM although there are a few extra things that need fixing (due, I think, to having gcc-4.7 on that box - rather than the fact that it's 64-bit).

Since you are not actually installing the OpenCV libraries into your 'system', in order to run the executable you will need to tell the dynamic linker where to find them - just for testing purposes I suggest you do that using LD_LIBRARY_PATH (it's oldskool, dirty, and frowned upon - but I think it's justified in this case) i.e.

```

steeldriver@alice-vm1:/usr/local/src/headtrack$ [COLOR=#0000ff]**LD_LIBRARY_PATH=../OpenCV-2.1.0/Build/lib/ ./headtrack**[/COLOR]
headtrack.c: Created socket. Destination = 127.0.0.1:49405!
Sorry, cannot open camera.
OpenCV Error: Null pointer (NULL array pointer is passed) in cvGetMat, file /usr/local/src/OpenCV-2.1.0/src/cxcore/cxarray.cpp, line 2376
terminate called after throwing an instance of 'cv::Exception'
  what():  /usr/local/src/OpenCV-2.1.0/src/cxcore/cxarray.cpp:2376: error: (-27) NULL array pointer is passed in function cvGetMat

Aborted
steeldriver@alice-vm1:/usr/local/src/headtrack$ 

```

As you can see it is bombing because I don't have any kind of camera / video device. It *may* bomb even *with* a valid camera since we had to exclude the video4linux component to get it to build - see how far you can get and we can review next steps.

---

### Post by paulemony on 2013-05-10
Assume you meant remove the duplicate headtrack subfile, but I deleted that already, so carried on, got this far:

```
paul@paul-desktop:/usr/local/src$ tree -L 1.
&#9500;&#9472;&#9472; headtrack
&#9500;&#9472;&#9472; OpenCV-2.1.0
&#9492;&#9472;&#9472; OpenCV-2.1-Readme.txt
```

Don't see **nlopt** or **optpp**, don't know if that matters. I replaced the Makefile in headtrack with the one you gave me (not sure if that's what I was supposed to do, and if it was what to do next):

```
paul@paul-desktop:/usr/local/src/headtrack$ makeMakefile:38: *** missing separator. Stop.



```

---

### Post by steeldriver on 2013-05-10
Ignore nlopt and optpp - they're just other things I happen to have in my /usr/local/src

The Makefile 'missing separators' thing is because of copy/paste issues - the forum has probably replaced the tabs (which are *essential* for Makefile rules) with spaces, you probably need to edit it manually so that it looks identical but wherever there's a build target followed by a rule, the rule needs to be indented with an actual tab character:

```

$(TRGT): $(OBJS)
[COLOR=#0000ff]<TAB>[/COLOR]$(CC) $(OBJS) $(LPATH) $(LIBS) -o $@


install: $(TRGT)
[COLOR=#0000ff]<TAB>[/COLOR]cp $(TRGT) $(INSTALLDIR)/$(TRGT)

uninstall: 
[COLOR=#0000ff]<TAB>[/COLOR]rm -f $(INSTALLDIR)/$(TRGT)


clean: 
[COLOR=#0000ff]<TAB>[/COLOR]rm -f $(OBJS)

cleaner: clean
[COLOR=#0000ff]<TAB>[/COLOR]rm -f $(TRGT)

cleanest: cleaner


```

---

### Post by paulemony on 2013-05-10
Not sure what you mean by "an actual tab character", Control+V enters those very words, I tried **^ **but that's not it.

---

### Post by steeldriver on 2013-05-10
Hi please run this on the Makefile that you copy/pasted

```
sed -i $'s/^ \+/\t/' Makefile
```

---

### Post by paulemony on 2013-05-10
OK, did that, ran "make", webcam connected, next brick wall, as predicted:

```
$:/usr/local/src/headtrack$ LD_LIBRARY_PATH=../OpenCV-2.1.0/Build/lib/ ./headtrackheadtrack.c: Created socket. Destination = 127.0.0.1:49405!


(Head Tracking:2723): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer


(Head Tracking:2723): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


(Head Tracking:2723): GStreamer-CRITICAL **: gst_bin_add_many: assertion `GST_IS_ELEMENT (element_1)' failed
OpenCV Error: Null pointer (NULL array pointer is passed) in cvGetMat, file /usr/local/src/OpenCV-2.1.0/src/cxcore/cxarray.cpp, line 2376
terminate called after throwing an instance of 'cv::Exception'
  what():  /usr/local/src/OpenCV-2.1.0/src/cxcore/cxarray.cpp:2376: error: (-27) NULL array pointer is passed in function cvGetMat


Aborted (core dumped)



```

---

### Post by steeldriver on 2013-05-10
OK let's see if I can attach a patch file here ... not sure if text attachments work on this forum

IF you can apply it, this patch should fix the build errors with the OpenCV libv4l components. It is based on the patch / bug report from the 2.2 branch here --> [https://code.ros.org/trac/opencv/changeset/5206](https://code.ros.org/trac/opencv/changeset/5206) but modified in a couple of places for slight differences between the 2.1.0 and 2.2 sources. [It also fixes a few errors due to missing 'unlink' macros when compiled under gcc-4.7 which I have left in even though they probably are not required for your platform (they only add a few '#include <unistd.h>' lines). Ideally I would split it into 2 separate patches, but that requires extra effort.]


To apply the patch, place it in your top level OpenCV-2.1.0 directory and then run

```
patch -p1 < patch-OpenCV-2.1.0-V4L.txt
```

You should see an output something like

```

patching file cvconfig.h.cmake
patching file include/opencv/cxcore.h
patching file src/highgui/cvcap.cpp
patching file src/highgui/cvcap_libv4l.cpp
patching file src/highgui/_highgui.h
patching file tests/cv/src/anearestneighbors.cpp
patching file tests/cxcore/src/aio.cpp
patching file tests/ml/src/slmltests.cpp

```

Then you can clean out your OpenCV-2.1.0 Build directory and try again, this time NOT excluding any default components

```

steeldriver@lap-t61p:/usr/local/src/OpenCV-2.1.0$ cd Build
steeldriver@lap-t61p:/usr/local/src/OpenCV-2.1.0/Build$ 
steeldriver@lap-t61p:/usr/local/src/OpenCV-2.1.0/Build$ rm -rf *
steeldriver@lap-t61p:/usr/local/src/OpenCV-2.1.0/Build$ 
steeldriver@lap-t61p:/usr/local/src/OpenCV-2.1.0/Build$ cmake -D OPENCV_EXTRA_C_FLAGS=-D__STDC_CONSTANT_MACROS ..

```

**[be extra careful that you know exactly where you are before executing the [FONT=courier new]rm -rf[/FONT] command !]**

Now you should be able to remake the OpenCV libs with V4L support (it won't include FFMPEG since that is off by default)

```
steeldriver@lap-t61p:/usr/local/src/OpenCV-2.1.0/Build$ make
```

If that works, go back to your headtrack directory and make that from scratch as well i.e.

```

steeldriver@lap-t61p:/usr/local/src/OpenCV-2.1.0/Build$ cd ../../headtrack/
steeldriver@lap-t61p:/usr/local/src/headtrack$ 
steeldriver@lap-t61p:/usr/local/src/headtrack$ make cleanest
rm -f headtrack.o
rm -f headtrack
steeldriver@lap-t61p:/usr/local/src/headtrack$ make

```

If headtrack doesn't work after that then there's nothing else I can think to try - unless you have more specific instructions from somewhere on how to build it

Good luck

[ATTACH]242433[/ATTACH]

**EDIT: I just remembered we already 'patched' /include/opencv/cxcore.h  manually (using 'sed')  - I created (and tested) the patch with respect to a completely unmolested copy of OpenCV-2.1.0 that I untarred from the original .bz2 file, so you may be better of starting again from that point i.e. untar a fresh copy, apply the patch, create the Build dir, cmake, make**

---

### Post by paulemony on 2013-05-11
For the record:

```
$:/usr/local/src/headtrack$ ./headtrack
headtrack.c: Created socket. Destination = 127.0.0.1:49405!
Sorry, cannot open camera.
OpenCV Error: Null pointer (NULL array pointer is passed) in cvGetMat, file /usr/local/src/OpenCV-2.1.0/src/cxcore/cxarray.cpp, line 2376
terminate called after throwing an instance of 'cv::Exception'
  what():  /usr/local/src/OpenCV-2.1.0/src/cxcore/cxarray.cpp:2376: error: (-27) NULL array pointer is passed in function cvGetMat



```

---

### Post by steeldriver on 2013-05-11
Well I picked up a webcam today (on sale this weekend! good timing)

The patched version is working for me - at least, it's getting as far as popping up a viewing window, I don't know what else is supposed to happen

I also noticed that the headtrack code can be patched quite simply to get it to build against OpenCV 2.3 (but I haven't had a chance to test that yet) so that might be a better route

---

### Post by paulemony on 2013-05-12
You mean just install v. 2.3.1-7 from Synaptic & run **sed -i '/#include "cxtypes.h"/i#include <stddef.h>' ../include/opencv/cxcore.h **
or somesuch?

---

### Post by steeldriver on 2013-05-12
No it will be a matter of adding a new parameter to each of the cvHaarDetectObjects calls and making sure you have the relevant 'translation packages' that let you use the original C API instead of the newer opencv2 C++ API

Before we dive in, can you please post the output of:

```
apt-cache policy libopencv-dev libcv-dev libopencv-highgui-dev libhighgui-dev
```

---

### Post by paulemony on 2013-05-12
```
:~$ apt-cache policy libopencv-dev libcv-dev libopencv-highgui-dev libhighgui-devlibopencv-dev:
  Installed: (none)
  Candidate: 2.3.1-7
  Version table:
     2.3.1-7 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
libcv-dev:
  Installed: (none)
  Candidate: 2.3.1-7
  Version table:
     2.3.1-7 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
libopencv-highgui-dev:
  Installed: (none)
  Candidate: 2.3.1-7
  Version table:
     2.3.1-7 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
libhighgui-dev:
  Installed: (none)
  Candidate: 2.3.1-7
  Version table:
     2.3.1-7 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages



```

---

### Post by steeldriver on 2013-05-12
OK that looks good

I'm not sure how far you got in installing 2.1.0 from source but we should probably at least try to run the uninstall to minimize the chances of confusing the package management system. So go to your OpenCV 2.1.0 Build directory and 

```

[COLOR=#a9a9a9]/usr/local/src/OpenCV-2.1.0-patched-V4L$[/COLOR] cd Build/
[COLOR=#a9a9a9]/usr/local/src/OpenCV-2.1.0-patched-V4L/Build$[/COLOR] sudo make uninstall 

```

It should give you an output something like

```

Scanning dependencies of target uninstall
.
.
.

```

For example mine gives

```

Scanning dependencies of target uninstall
CMake Error at cmake_uninstall.cmake:6 (MESSAGE):
  Cannot find install manifest:
  "/usr/local/src/OpenCV-2.1.0-patched-V4L/Build/install_manifest.txt"


make[3]: *** [CMakeFiles/uninstall] Error 1
make[2]: *** [CMakeFiles/uninstall.dir/all] Error 2
make[1]: *** [CMakeFiles/uninstall.dir/rule] Error 2
make: *** [uninstall] Error 2

```

because I didn't actually install anything. If it either (1) finds no manifest (like mine) or finds it and successfully deletes everything then you can move on and install the above packages from the repositories, either via a package manager such as Synaptic or just with apt-get:

```
sudo apt-get install libopencv-dev libopencv-highgui-dev libcv-dev libhighgui-dev
```

Then you can EITHER start with a completely fresh copy of headtrack and patch both the headtrack.c source code and Makefile, or start from where you are and just patch headtrack.c - the only change I had to make to headtrack.c is that the cvHaarDetectObjects function now takes a max size as well as a min size for the target: I don't know what the 'right' thing to put in there is, but it seems to work OK if you just set the max size equal to the size of the image:

i.e.

```

      faces = cvHaarDetectObjects( imggray, cascade, store, HAAR_SCALE, 2, 
                                   BIGGEST + ROUGH, SEARCH_SIZE);


```
becomes
```

      faces = cvHaarDetectObjects( imggray, cascade, store, HAAR_SCALE, 2, 
                                   BIGGEST + ROUGH, SEARCH_SIZE[COLOR=#0000ff]**, cvGetSize(imggray)**[/COLOR]);


```

and so on (there are 3 such replacements in total). You can edit them manually or apply one of the attached patches; either

```

[COLOR=#a9a9a9]t61p:/usr/local/src$[/COLOR] cd headtrack
[COLOR=#a9a9a9]t61p:/usr/local/src/headtrack$[/COLOR] patch -p1 < ../patch-headtrack-OpenCV2.3.txt
[COLOR=#a9a9a9]t61p:/usr/local/src/headtrack$[/COLOR] make

```

or if you want to start over and patch the source code and the original Makefile (I have tidied up the Makefile and added back the flightgear stuff since yesterday so that would be my recommendation)

```

[COLOR=#a9a9a9] t61p:/usr/local/src$[/COLOR] cd headtrack
[COLOR=#a9a9a9]t61p:/usr/local/src/headtrack$[/COLOR] patch -p1 < ../patch-headtrack-OpenCV2.3-newmake.txt
[COLOR=#a9a9a9]t61p:/usr/local/src/headtrack$[/COLOR] make

```

both assuming that the patch file(s) are in the /usr/local/src directory on the same level as the top level headtrack directory. 

Since this way builds against properly installed system libraries, there's no need for the LD_LIBRARY_PATH hack, if 'make' succeeds you should be able to run it with

```
[COLOR=#a9a9a9]t61p:/usr/local/src/headtrack$[/COLOR] ./headtrack
```

Or with the new Makefile you can 'make install' which will put it in the /usr/local/bin directory which is probably on your path so you can invoke from anywhere as 

```
[COLOR=#a9a9a9]$[/COLOR] headtrack
```

Good luck

---

### Post by paulemony on 2013-05-12
I feel a bit like someone learning a new language who's confronted with a native speaker who talks so fast he can't keep up! I've installed OpenCV-2.3 which is in /usr/include (in fact there are 2 folders, **opencv **which just includes a few files, and **opencv2  **which seems to be the full monty, not sure if the 1st one is a hangover from previous install, & if so what to do with it), and reinstalled headtrack back into /usr/local/src but slightly confused as to what to do next. You mention "attached patches" but I don't see them my side.

---

### Post by steeldriver on 2013-05-12
Oops here you go, copy either / both of these into your /usr/local/src directory and then run the corresponding patch command that I posted above -  depending whether you want the new Makefile or just the source code patch

---

### Post by paulemony on 2013-05-12
I put **[COLOR=#000000][FONT=Ubuntu Mono]patch-headtrack-OpenCV2.3-newmake.txt [/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]into[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/usr/local/src & ran

[/FONT][/COLOR]```
$**[COLOR=#a9a9a9][FONT=Ubuntu Mono]:/usr/local/src/headtrack$ [/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]patch -p1 < ../patch-headtrack-OpenCV2.3-newmake.txt
[/FONT][/COLOR]

```
[COLOR=#000000][FONT=Ubuntu Mono]
But then I get
[/FONT][/COLOR]

```
$:/usr/local/src/headtrack$ make
gcc -std=c99 -Wall -Wextra -msse -msse2 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/X11  -pthread -I/usr/local/include/opencv -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12    -m64 -mtune=amdfam10 -O3   -c -o headtrack.o headtrack.c
In file included from /usr/local/include/opencv/cv.h:1625:0,
                 from headtrack.c:42:
/usr/local/include/opencv/cvcompat.h: In function ‘cvConvexHull’:
/usr/local/include/opencv/cvcompat.h:383:38: warning: unused parameter ‘bound_rect’ [-Wunused-parameter]
/usr/local/include/opencv/cvcompat.h: In function ‘cvMinAreaRect’:
/usr/local/include/opencv/cvcompat.h:425:5: warning: left-hand operand of comma expression has no effect [-Wunused-value]
/usr/local/include/opencv/cvcompat.h:425:5: warning: left-hand operand of comma expression has no effect [-Wunused-value]
/usr/local/include/opencv/cvcompat.h:425:5: warning: left-hand operand of comma expression has no effect [-Wunused-value]
/usr/local/include/opencv/cvcompat.h:425:5: warning: statement with no effect [-Wunused-value]
/usr/local/include/opencv/cvcompat.h: In function ‘cvFindFundamentalMatrix’:
/usr/local/include/opencv/cvcompat.h:542:48: warning: unused parameter ‘method’ [-Wunused-parameter]
/usr/local/include/opencv/cvcompat.h: In function ‘cvFindChessBoardCornerGuesses’:
/usr/local/include/opencv/cvcompat.h:573:55: warning: unused parameter ‘thresharr’ [-Wunused-parameter]
/usr/local/include/opencv/cvcompat.h:574:47: warning: unused parameter ‘storage’ [-Wunused-parameter]
/usr/local/include/opencv/cvcompat.h: In function ‘cvFindExtrinsicCameraParams’:
/usr/local/include/opencv/cvcompat.h:638:12: warning: unused parameter ‘image_size’ [-Wunused-parameter]
/usr/local/include/opencv/cvcompat.h: In function ‘cvFindExtrinsicCameraParams_64d’:
/usr/local/include/opencv/cvcompat.h:663:12: warning: unused parameter ‘image_size’ [-Wunused-parameter]
/usr/local/include/opencv/cvcompat.h: In function ‘cvUnDistortOnce’:
/usr/local/include/opencv/cvcompat.h:757:37: warning: unused parameter ‘interpolate’ [-Wunused-parameter]
/usr/local/include/opencv/cvcompat.h: In function ‘cvUnDistortInit’:
/usr/local/include/opencv/cvcompat.h:767:46: warning: unused parameter ‘src’ [-Wunused-parameter]
/usr/local/include/opencv/cvcompat.h:770:37: warning: unused parameter ‘interpolate’ [-Wunused-parameter]
/usr/local/include/opencv/cvcompat.h: In function ‘cvUnDistort’:
/usr/local/include/opencv/cvcompat.h:785:34: warning: unused parameter ‘interpolate’ [-Wunused-parameter]
headtrack.c: In function ‘main’:
headtrack.c:216:36: error: too many arguments to function ‘cvHaarDetectObjects’
/usr/local/include/opencv/cv.h:1239:15: note: declared here
headtrack.c:227:39: error: too many arguments to function ‘cvHaarDetectObjects’
/usr/local/include/opencv/cv.h:1239:15: note: declared here
headtrack.c:235:39: error: too many arguments to function ‘cvHaarDetectObjects’
/usr/local/include/opencv/cv.h:1239:15: note: declared here
headtrack.c:105:7: warning: variable ‘new_transmitterthread’ set but not used [-Wunused-but-set-variable]
headtrack.c: In function ‘init’:
headtrack.c:395:7: warning: statement with no effect [-Wunused-value]
headtrack.c: In function ‘transmitter’:
headtrack.c:426:32: warning: unused parameter ‘arg’ [-Wunused-parameter]
headtrack.c: At top level:
/usr/local/include/opencv/cxtypes.h:236:17: warning: ‘cvFloor’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:254:17: warning: ‘cvCeil’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:274:15: warning: ‘cvIsNaN’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:289:15: warning: ‘cvIsInf’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:308:17: warning: ‘cvRNG’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:324:18: warning: ‘cvRandReal’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:662:20: warning: ‘cvmGet’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:697:15: warning: ‘cvIplDepth’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:872:20: warning: ‘cvRectToROI’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:885:20: warning: ‘cvROIToRect’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:906:28: warning: ‘cvTermCriteria’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:958:26: warning: ‘cvPointTo32f’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:983:26: warning: ‘cvPoint3D32f’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:1003:26: warning: ‘cvPoint2D64f’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:1023:26: warning: ‘cvPoint3D64f’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:1062:25: warning: ‘cvSize2D32f’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:1138:22: warning: ‘cvRealScalar’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxtypes.h:1657:22: warning: ‘cvAttrList’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:153:18: warning: ‘cvDecRefData’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:174:17: warning: ‘cvIncRefData’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:208:20: warning: ‘cvGetRow’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:219:20: warning: ‘cvGetCol’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:248:18: warning: ‘cvReleaseMatND’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:271:25: warning: ‘cvGetNextSparseNode’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:521:18: warning: ‘cvSubS’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1083:18: warning: ‘cvCloneSeq’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1126:23: warning: ‘cvSetNew’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1141:17: warning: ‘cvSetRemoveByPtr’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1156:22: warning: ‘cvGetSetElem’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1328:18: warning: ‘cvEllipseBox’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1421:18: warning: ‘cvFont’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1678:15: warning: ‘cvReadIntByName’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1693:18: warning: ‘cvReadRealByName’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1707:23: warning: ‘cvReadStringByName’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxcore.h:1719:17: warning: ‘cvReadByName’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxmisc.h:214:17: warning: ‘cvAlignPtr’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxmisc.h:220:15: warning: ‘cvAlign’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cxmisc.h:226:20: warning: ‘cvGetMatSize’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:628:24: warning: ‘cvCreateSubdivDelaunay2D’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:663:28: warning: ‘cvSubdiv2DNextEdge’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:669:28: warning: ‘cvSubdiv2DRotateEdge’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:674:28: warning: ‘cvSubdiv2DSymEdge’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:679:28: warning: ‘cvSubdiv2DGetEdge’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:687:30: warning: ‘cvSubdiv2DEdgeOrg’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:694:30: warning: ‘cvSubdiv2DEdgeDst’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:701:20: warning: ‘cvTriangleArea’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:871:18: warning: ‘cvCalcHist’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:1111:23: warning: ‘cvSURFPoint’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:1184:26: warning: ‘cvStarKeypoint’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cv.h:1203:32: warning: ‘cvStarDetectorParams’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:110:17: warning: ‘cvMatArray’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:126:18: warning: ‘cvMean’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:133:19: warning: ‘cvSumPixels’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:139:17: warning: ‘cvMean_StdDev’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:153:16: warning: ‘cvmPerspectiveProject’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:164:16: warning: ‘cvFillImage’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:213:18: warning: ‘cvRandInit’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:248:16: warning: ‘cvbRand’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:255:17: warning: ‘cvbCartToPolar’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:271:17: warning: ‘cvbFastArctan’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:285:18: warning: ‘cvbSqrt’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:295:18: warning: ‘cvbInvSqrt’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:305:18: warning: ‘cvbReciprocal’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:315:18: warning: ‘cvbFastExp’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:323:18: warning: ‘cvbFastLog’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:331:20: warning: ‘cvContourBoundingRect’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:337:18: warning: ‘cvPseudoInverse’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:382:16: warning: ‘cvConvexHull’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:407:16: warning: ‘cvMinAreaRect’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:432:18: warning: ‘cvFitLine3D’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:442:18: warning: ‘cvFitLine2D’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:452:17: warning: ‘cvFitEllipse’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:460:18: warning: ‘cvProject3D’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:503:17: warning: ‘cvHoughLines’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:515:17: warning: ‘cvHoughLinesP’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:528:17: warning: ‘cvHoughLinesSDiv’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:541:18: warning: ‘cvFindFundamentalMatrix’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:573:1: warning: ‘cvFindChessBoardCornerGuesses’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:584:16: warning: ‘cvCalibrateCamera’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:609:16: warning: ‘cvCalibrateCamera_64d’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:637:16: warning: ‘cvFindExtrinsicCameraParams’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:662:16: warning: ‘cvFindExtrinsicCameraParams_64d’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:691:17: warning: ‘cvRodrigues’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:702:17: warning: ‘cvProjectPoints’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:737:17: warning: ‘cvProjectPointsSimple’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:767:16: warning: ‘cvUnDistortInit’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:783:17: warning: ‘cvUnDistort’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:798:19: warning: ‘cvCalcEMD’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:812:18: warning: ‘cvKMeans’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:826:17: warning: ‘cvStartScanGraph’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:841:18: warning: ‘cvEndScanGraph’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:860:18: warning: ‘cvLineAA’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:866:18: warning: ‘cvCircleAA’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:872:18: warning: ‘cvEllipseAA’ defined but not used [-Wunused-function]
/usr/local/include/opencv/cvcompat.h:881:18: warning: ‘cvPolyLineAA’ defined but not used [-Wunused-function]
headtrack.c:421:16: warning: ‘decodeFloat’ defined but not used [-Wunused-function]
make: *** [headtrack.o] Error 1



```

---

### Post by steeldriver on 2013-05-12
Hmm... so unfortunately it looks like pkg-config still thinks you want to use the version of opencv that you installed manually into /usr/local - I had hoped that either (1) your 'make install' in OpenCV-2.1.0 hadn't got as far as altering the pkg-config database or (2) the 'sudo make uninstall' in /usr/local/src/OpenCV-2.1.0/Build would revert that or (3) the subsequent apt-get install would have overwritten it with the correct 2.3 location (which should be /usr/include)

Did you make a note of the output from 'make uninstall' by any chance?

EDIT: what is the output of

```
pkg-config --modversion opencv
```

and

```
echo $PKG_CONFIG_PATH
```

---

### Post by paulemony on 2013-05-12
```
$:~$ pkg-config --modversion opencv2.1.0



```

Anything to do with the two opencv folders in /usr/include?

---

### Post by joco1500 on 2013-05-12
```
sudo install ______________
```

---

### Post by steeldriver on 2013-05-12
No unfortunately - we **want **it to be to do with the two folders in /usr/include but it is stubbornly pointing us to the one folder in /usr/**local**/include - if everything is configured correctly you should have seen

```

$ pkg-config --modversion opencv
**2.3.1**

```

Can you also post the output of

```
dpkg -l | grep -E 'libopencv-.*-dev'
```

---

### Post by paulemony on 2013-05-12
```
$:~$ dpkg -l | grep -E 'libopencv-.*-dev'ii  libopencv-calib3d-dev                   2.3.1-7                                              development files for libopencv-calib3d
ii  libopencv-contrib-dev                   2.3.1-7                                              development files for libopencv-contrib
ii  libopencv-core-dev                      2.3.1-7                                              development files for libopencv-core
ii  libopencv-features2d-dev                2.3.1-7                                              development files for libopencv-features2d
ii  libopencv-flann-dev                     2.3.1-7                                              development files for libopencv-flann
ii  libopencv-gpu-dev                       2.3.1-7                                              development files for libopencv-gpu
ii  libopencv-highgui-dev                   2.3.1-7                                              development files for libopencv-highgui
ii  libopencv-imgproc-dev                   2.3.1-7                                              development files for libopencv-imgproc
ii  libopencv-legacy-dev                    2.3.1-7                                              development files for libopencv-legacy
ii  libopencv-ml-dev                        2.3.1-7                                              development files for libopencv-ml
ii  libopencv-objdetect-dev                 2.3.1-7                                              development files for libopencv-objdetect
ii  libopencv-video-dev                     2.3.1-7                                              development files for libopencv-video



```

---

### Post by steeldriver on 2013-05-12
Well I don't really know why it hasn't worked for you - I just went around the loop


[LIST]
[*]purged libopencv* 
[*]did a sudo make install in my OpenCV-2.1.0 directory 
[/LIST]

Sure enough, that forced pkg-config to pick up the 2.1.0 version, fwiw it puts the pc file in /usr/**local/lib**/opencv.pc 


[LIST]
[*]reinstalled libopencv-dev 
[/LIST]

At this point pkg-config is still showing the version as 2.1.0 although I confirmed that a new pc file gets installed as /usr/**lib**/opencv.pc - presumably the default search order places /usr/local ahead of /usr in the search path - I thought it should be possible to override that by exporting a PKG_CONFIG_PATH=/usr/lib but it doesn't seem to work.

However I then did


[LIST]
[*]sudo make **uninstall** in my OpenCV-2.1.0 Build directory 
[/LIST]

and the pesky /usr/**local/lib**/opencv.pc file was deleted as it should be, after which I was able to build headtrack against libopencv 2.3 as before.

So I guess the puzzle is why **sudo make uninstall** didn't work to fully remove the 2.1.0 references for you - maybe try it one more time and make a careful note of any error messages? Remember that when you issue that command, you need to be in the Build directory that we created with mkdir way back when. You can use

```
find /usr -name 'opencv.pc'
```

to flush out any other opencv.pc files that may be lurking - it will also tell us if 2.3 successfully installed its opencv.pc in /usr/lib

We could use absolute paths in the headtrack Makefile instead of relying on pkg-config (or we could just manually delete the stuff in /usr/local) - but I'd rather fix your system properly so you don't have other build problems down the line. Your call though.

---

### Post by paulemony on 2013-05-13
I think you've cracked it! After sudo make uninstall I ran

```
$-desktop:/usr/local/src/headtrack$ make
gcc -std=c99 -Wall -Wextra -msse -msse2 -fomit-frame-pointer -fno-strict-aliasing -I/usr/include/X11  -pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/opencv    -m64 -mtune=amdfam10 -O3   -c -o headtrack.o headtrack.c
headtrack.c: In function ‘main’:
headtrack.c:105:7: warning: variable ‘new_transmitterthread’ set but not used [-Wunused-but-set-variable]
headtrack.c: In function ‘init’:
headtrack.c:395:7: warning: statement with no effect [-Wunused-value]
headtrack.c: In function ‘transmitter’:
headtrack.c:426:32: warning: unused parameter ‘arg’ [-Wunused-parameter]
headtrack.c: At top level:
headtrack.c:421:16: warning: ‘decodeFloat’ defined but not used [-Wunused-function]
gcc headtrack.o  -pthread -lopencv_core -lopencv_imgproc -lopencv_highgui -lopencv_ml -lopencv_video -lopencv_features2d -lopencv_calib3d -lopencv_objdetect -lopencv_contrib -lopencv_legacy -lopencv_flann -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0   -o headtrack


$:/usr/local/src/headtrack$ ./headtrack
headtrack.c: Created socket. Destination = 127.0.0.1:49405!
VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument



```

and got an image, don't know if the "Invalid argument" means there's any fine tuning left to be done (the image is very laggy), otherwise thanks v.much for your expertise & patience, I shall move on to the problem of getting it to work in Flightgear...................

---

### Post by paulemony on 2013-05-13
P.S. google suggests that there's a "Waitkey" value in opencv that needs adjusting but nowhere do I find a simple answer on how to do this, at least in Ubuntu, I think opencv has a gui that would do it but again I don't know how to open it, any suggestions welcome, otherwise I'll start a new thread. Another thing I don't know/can't remember is how to mark this one as solved, it isn't blazingly obvious!

---

### Post by steeldriver on 2013-05-13
WAHOO! Glad we got there finally - well done for sticking at it

I also get a bunch of "VIDIOC_QUERYMENU: Invalid argument" errors when it starts up - but nothing once it starts tracking. So if it's a matter of putting a cvWaitKey delay in I would guess it needs to be outside the main 'while' loop - but I don't know where. OTOH it might be something that needs fixing in the underlying video layer (somewhere in video4linux).

---

