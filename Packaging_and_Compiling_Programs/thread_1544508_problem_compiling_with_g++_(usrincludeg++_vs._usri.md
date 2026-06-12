---
title: "problem compiling with g++ (/usr/include/g++/ vs. /usr/include/c++/)"
date: 2010-08-02
forum: Packaging and Compiling Programs
---

### Post by crypticlynx on 2010-08-02
Hi!

I hope I am in the right forum here. I tried to compile a program and hit errors that seem fairly simple to solve but I just can't see the solution...
After "make" I get this:
g++  -o ccdOpsLite .obj/main.o .obj/csbigcam.o .obj/csbigimg.o .obj/imagefip.o .obj/showimg.o .obj/mainform.o .obj/cameracontrol.o .obj/contrastform.o .obj/imageinfoform.o .obj/linksetupform.o .obj/qmake_image_collection.o .obj/moc_imagefip.o .obj/moc_showimg.o .obj/moc_mainform.o .obj/moc_cameracontrol.o .obj/moc_contrastform.o .obj/moc_imageinfoform.o .obj/moc_linksetupform.o   -L/usr/share/qt3/lib -L/usr/X11R6/lib libcfitsio.so -lsbigudrv -lqt-mt -lXext -lX11 -lm -lpthread
.obj/csbigcam.o: In function `_Alloc_hider':
/usr/include/g++/bits/basic_string.h:325: undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_S_empty_rep_storage'
...
It just continues with errors of undefined references to std::bla...
I have g++ installed but the directory /usr/include/g++/ doesn't exist on my computer. However there is a directory /usr/include/c++/4.4/bits/ that contains for an example basic_string.h
Any idea how I can get the program to compile??

PS: I don't have much experience in C and none in C++...

---

### Post by crypticlynx on 2010-08-04
Perhaps I wasn't precise enough. Before make I had to run qmake:
```
qmake -o MakeFile ccdOpsLite.pro 
```
Also the code was written using qt3. I have both qt3 and qt4 installed on my computer. My OS is ubuntu 10.04 32bit.
Is there any clue on how solve the errors??
I tried using qt creator but it apparently only works for qt4 :-(

---

### Post by SevenMachines on 2010-08-06
I'm guessing this is quite old so it may be far from healthy but it compiles if you remove the old objects that are aparently included in the tarball (in .obj)

 add 
#include <cstring> 
to csbigcam.cpp

then
$ qmake -o Makefile ccdOpsLite.pro

# clean out the old objects
$ make clean  
$ make

---

### Post by crypticlynx on 2010-09-22
Thanks for the answer! I haven't checked this thread in a while...
What exactly do you mean by "far from healthy"? Isn't cstring just allowing a different way of handling strings (through arrays)?
Anyways the program compiles now and it seems to run ok: I can connect the camera, grab an image and view it. The help function for some reason doesn't work...

---

### Post by SevenMachines on 2010-09-22
Hi there. by far from healthy i just meant that it seems old and un-maintained so it might have problems with newer software, possible why help doesnt work and so on.

The <cstring> include is needed because [from gcc 4.3 onwards there was a clean up of gcc's headers]("http://gcc.gnu.org/gcc-4.3/porting_to.html"), this meant that some headers that were included implicitly now aren't and have to be added explicitly to the files that need them. 
cstring is cpp's interface to the standard library's string functions and not especially anything to do with arrays.

Glad it works!

---

### Post by crypticlynx on 2010-09-22
Hi! It seems I have been a little too optimistic: The program unfortunately also is unable to save pictures in the desired FITS-format (instead it quits with a segmentation fault and leaves an empty file). I think I better look for a different software. 

It really seems like there is a lot of dust on the linux stuff of sbig (camera producer). Took me forever just to install the driver...

But thank you very much anyways!

---

