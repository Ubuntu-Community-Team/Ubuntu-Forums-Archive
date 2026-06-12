---
title: "CImg.h with Eclipse when debugging  with this error"
date: 2014-12-13
forum: Programming Talk
---

### Post by ahmed.abasy on 2014-12-13
18:03:37 **** Incremental Build of configuration Debug for project testImage ****
make all 
Building target: testImage
Invoking: GCC C++ Linker
g++  -o "testImage"  ./test.o   
./test.o: In function `cimg_library::cimg::X11_info::X11_info()':
/home/obasy/workspace/testImage/Debug/../CImg.h:2527: undefined reference to `XInitThreads'
./test.o: In function `cimg_library::cimg::X11_info::~X11_info()':
/home/obasy/workspace/testImage/Debug/../CImg.h:2539: undefined reference to `pthread_cancel'
./test.o: In function `cimg_library::cimg::Mutex_info::trylock(unsigned int)':
/home/obasy/workspace/testImage/Debug/../CImg.h:2582: undefined reference to `pthread_mutex_trylock'
./test.o: In function `cimg_library::CImgDisplay::screen_width()':
/home/obasy/workspace/testImage/Debug/../CImg.h:7314: undefined reference to `XOpenDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7318: undefined reference to `XCloseDisplay'
./test.o: In function `cimg_library::CImgDisplay::screen_height()':
/home/obasy/workspace/testImage/Debug/../CImg.h:7335: undefined reference to `XOpenDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7339: undefined reference to `XCloseDisplay'
./test.o: In function `cimg_library::CImgDisplay::_handle_events(_XEvent const*)':
/home/obasy/workspace/testImage/Debug/../CImg.h:7366: undefined reference to `XUnmapWindow'
/home/obasy/workspace/testImage/Debug/../CImg.h:7372: undefined reference to `XCheckWindowEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7377: undefined reference to `XResizeWindow'
/home/obasy/workspace/testImage/Debug/../CImg.h:7387: undefined reference to `XCheckWindowEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7391: undefined reference to `XGetWindowAttributes'
/home/obasy/workspace/testImage/Debug/../CImg.h:7392: undefined reference to `XSync'
/home/obasy/workspace/testImage/Debug/../CImg.h:7393: undefined reference to `XSetInputFocus'
/home/obasy/workspace/testImage/Debug/../CImg.h:7405: undefined reference to `XCheckWindowEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7418: undefined reference to `XCheckWindowEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7422: undefined reference to `XLookupString'
/home/obasy/workspace/testImage/Debug/../CImg.h:7427: undefined reference to `XQueryKeymap'
/home/obasy/workspace/testImage/Debug/../CImg.h:7432: undefined reference to `XLookupString'
/home/obasy/workspace/testImage/Debug/../CImg.h:7437: undefined reference to `XCheckWindowEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7443: undefined reference to `XCheckWindowEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7448: undefined reference to `XCheckWindowEvent'
./test.o: In function `cimg_library::CImgDisplay::_events_thread(void*)':
/home/obasy/workspace/testImage/Debug/../CImg.h:7464: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7465: undefined reference to `XCheckTypedEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7469: undefined reference to `XCheckMaskEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7474: undefined reference to `XUnlockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7475: undefined reference to `pthread_testcancel'
./test.o: In function `cimg_library::CImgDisplay::_set_colormap(unsigned long&, unsigned int)':
/home/obasy/workspace/testImage/Debug/../CImg.h:7512: undefined reference to `XStoreColors'
./test.o: In function `cimg_library::CImgDisplay::_map_window()':
/home/obasy/workspace/testImage/Debug/../CImg.h:7520: undefined reference to `XMapRaised'
/home/obasy/workspace/testImage/Debug/../CImg.h:7522: undefined reference to `XWindowEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7529: undefined reference to `XGetWindowAttributes'
/home/obasy/workspace/testImage/Debug/../CImg.h:7530: undefined reference to `XSync'
./test.o: In function `cimg_library::CImgDisplay::_paint(bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:7551: undefined reference to `XSendEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7558: undefined reference to `XPutImage'
./test.o: In function `cimg_library::CImgDisplay::_init_fullscreen()':
/home/obasy/workspace/testImage/Debug/../CImg.h:7666: undefined reference to `XCreateWindow'
/home/obasy/workspace/testImage/Debug/../CImg.h:7671: undefined reference to `XCreateImage'
/home/obasy/workspace/testImage/Debug/../CImg.h:7673: undefined reference to `XSelectInput'
/home/obasy/workspace/testImage/Debug/../CImg.h:7674: undefined reference to `XMapRaised'
/home/obasy/workspace/testImage/Debug/../CImg.h:7675: undefined reference to `XWindowEvent'
/home/obasy/workspace/testImage/Debug/../CImg.h:7682: undefined reference to `XPutImage'
/home/obasy/workspace/testImage/Debug/../CImg.h:7685: undefined reference to `XGetWindowAttributes'
/home/obasy/workspace/testImage/Debug/../CImg.h:7686: undefined reference to `XSync'
./test.o: In function `cimg_library::CImgDisplay::_desinit_fullscreen()':
/home/obasy/workspace/testImage/Debug/../CImg.h:7693: undefined reference to `XUngrabKeyboard'
/home/obasy/workspace/testImage/Debug/../CImg.h:7703: undefined reference to `XDestroyWindow'
./test.o: In function `cimg_library::CImgDisplay::_assign(unsigned int, unsigned int, char const*, unsigned int, bool, bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:7731: undefined reference to `XOpenDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7745: undefined reference to `XVisualIDFromVisual'
/home/obasy/workspace/testImage/Debug/../CImg.h:7747: undefined reference to `XGetVisualInfo'
/home/obasy/workspace/testImage/Debug/../CImg.h:7750: undefined reference to `XFree'
/home/obasy/workspace/testImage/Debug/../CImg.h:7752: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7754: undefined reference to `pthread_create'
/home/obasy/workspace/testImage/Debug/../CImg.h:7755: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7774: undefined reference to `XCreateWindow'
/home/obasy/workspace/testImage/Debug/../CImg.h:7776: undefined reference to `XCreateSimpleWindow'
/home/obasy/workspace/testImage/Debug/../CImg.h:7780: undefined reference to `XSelectInput'
/home/obasy/workspace/testImage/Debug/../CImg.h:7782: undefined reference to `XStoreName'
/home/obasy/workspace/testImage/Debug/../CImg.h:7784: undefined reference to `XCreateColormap'
/home/obasy/workspace/testImage/Debug/../CImg.h:7786: undefined reference to `XSetWindowColormap'
/home/obasy/workspace/testImage/Debug/../CImg.h:7790: undefined reference to `XAllocClassHint'
/home/obasy/workspace/testImage/Debug/../CImg.h:7793: undefined reference to `XSetClassHint'
/home/obasy/workspace/testImage/Debug/../CImg.h:7794: undefined reference to `XFree'
/home/obasy/workspace/testImage/Debug/../CImg.h:7831: undefined reference to `XCreateImage'
/home/obasy/workspace/testImage/Debug/../CImg.h:7834: undefined reference to `XInternAtom'
/home/obasy/workspace/testImage/Debug/../CImg.h:7835: undefined reference to `XInternAtom'
/home/obasy/workspace/testImage/Debug/../CImg.h:7836: undefined reference to `XSetWMProtocols'
/home/obasy/workspace/testImage/Debug/../CImg.h:7838: undefined reference to `XGrabKeyboard'
/home/obasy/workspace/testImage/Debug/../CImg.h:7841: undefined reference to `XUnlockDisplay'
./test.o: In function `cimg_library::CImgDisplay::assign()':
/home/obasy/workspace/testImage/Debug/../CImg.h:7848: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7858: undefined reference to `XDestroyWindow'
/home/obasy/workspace/testImage/Debug/../CImg.h:7872: undefined reference to `XFreeColormap'
/home/obasy/workspace/testImage/Debug/../CImg.h:7874: undefined reference to `XSync'
/home/obasy/workspace/testImage/Debug/../CImg.h:7886: undefined reference to `XUnlockDisplay'
./test.o: In function `cimg_library::CImgDisplay::resize(int, int, bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:7943: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7947: undefined reference to `XResizeWindow'
/home/obasy/workspace/testImage/Debug/../CImg.h:7948: undefined reference to `XGetWindowAttributes'
/home/obasy/workspace/testImage/Debug/../CImg.h:7960: undefined reference to `XUnlockDisplay'
./test.o: In function `cimg_library::CImgDisplay::show()':
/home/obasy/workspace/testImage/Debug/../CImg.h:7983: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:7987: undefined reference to `XUnlockDisplay'
./test.o: In function `cimg_library::CImgDisplay::move(int, int)':
/home/obasy/workspace/testImage/Debug/../CImg.h:8007: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:8008: undefined reference to `XMoveWindow'
/home/obasy/workspace/testImage/Debug/../CImg.h:8011: undefined reference to `XUnlockDisplay'
./test.o: In function `cimg_library::CImgDisplay::paint(bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:8083: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:8085: undefined reference to `XUnlockDisplay'
./test.o: In function `void cimg_library::CImgDisplay::_resize<unsigned char>(unsigned char, unsigned int, unsigned int, bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:7618: undefined reference to `XCreateImage'
./test.o: In function `void cimg_library::CImgDisplay::_resize<unsigned short>(unsigned short, unsigned int, unsigned int, bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:7618: undefined reference to `XCreateImage'
./test.o: In function `void cimg_library::CImgDisplay::_resize<unsigned int>(unsigned int, unsigned int, unsigned int, bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:7618: undefined reference to `XCreateImage'
./test.o: In function `cimg_library::CImgDisplay& cimg_library::CImgDisplay::render<double>(cimg_library::CImg<double> const&, bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:8110: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:8409: undefined reference to `XUnlockDisplay'
./test.o: In function `cimg_library::CImgDisplay& cimg_library::CImgDisplay::render<unsigned char>(cimg_library::CImg<unsigned char> const&, bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:8110: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:8409: undefined reference to `XUnlockDisplay'
./test.o: In function `cimg_library::CImgDisplay& cimg_library::CImgDisplay::render<unsigned int>(cimg_library::CImg<unsigned int> const&, bool)':
/home/obasy/workspace/testImage/Debug/../CImg.h:8110: undefined reference to `XLockDisplay'
/home/obasy/workspace/testImage/Debug/../CImg.h:8409: undefined reference to `XUnlockDisplay'
collect2: error: ld returned 1 exit status
make: *** [testImage] Error 1


18:03:37 Build Finished (took 202ms)

---

### Post by steeldriver on 2014-12-13
Hello and welcome to the forums

Your command

```

g++  -o "testImage"  ./test.o

```

doesn't tell g++ which additional libraries to link in order to create the executable target. If you are using eclipse, you will need to configure these in the C/C++ build settings (probably "C/C++ Build" -> "Settings").

---

### Post by schragge on 2014-12-13
You [need to link with X11 libs]("http://cimg.sourceforge.net/reference/group__cimg__overview.html#s3").
```
g++ -o testImage -O2 -L/usr/X11R6/lib -lm -lpthread -lX11  ./test.o
```

---

### Post by ahmed.abasy on 2014-12-13
/usr/bin/ld: cannot find -lx11
collect2: error: ld returned 1 exit status

---

### Post by steeldriver on 2014-12-13
Letter-case is significant in Linux - it needs to be a capital (upper-case) X I think
```
-l[COLOR=#0000ff]**X**[/COLOR]11
```

---

### Post by ahmed.abasy on 2014-12-13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 0 has invalid symbol index 11
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 1 has invalid symbol index 12
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 2 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 3 has invalid symbol index 2
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 4 has invalid symbol index 11
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 5 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 6 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 7 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 8 has invalid symbol index 12
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 9 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 10 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 11 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 12 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 13 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 14 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 15 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 16 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 17 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 18 has invalid symbol index 13
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 19 has invalid symbol index 21
/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_line): relocation 0 has invalid symbol index 2
/usr/lib/gcc/x86_64-linux-gnu/4.9/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: error: ld returned 1 exit status

This is the message that appeared !

---

### Post by schragge on 2014-12-13
This error means the linker is not able to find the definition of main() function anywhere in your source code.

---

### Post by ahmed.abasy on 2014-12-13
23:08:11 **** Incremental Build of configuration Debug for project testImage ****
make all 
Building file: ../test.cpp
Invoking: GCC C++ Compiler
g++ -I"/home/obasy/workspace/testImage" -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"test.d" -MT"test.d" -o "test.o" "../test.cpp"
Finished building: ../test.cpp
 
Building target: testImage
Invoking: GCC C++ Linker
g++ -L"/home/obasy/workspace/testImage" -o "testImage"  ./test.o   -lCImg.h
/usr/bin/ld: cannot find -lCImg.h
collect2: error: ld returned 1 exit status
make: *** [testImage] Error 1


23:08:18 Build Finished (took 7s.676ms)

Now this is the error that appeared !!

---

### Post by steeldriver on 2014-12-13
Well CImg.h is a *header file* not a library - you don't link header files

Perhaps it would be easier to help you if you gave us some context - what exactly are you trying to build? did you write the code yourself or are you trying to build a source package that you obtained from somewhere?

---

### Post by tstdlvl on 2015-10-20
Hello, I have the same problem, but do not know how to apply the solution.
I am using Ubuntu 14.04 LTS, and Eclipse Kepler. My code is very simple:

```
// Std Lib
#include <iostream>
#include <stdlib.h>

// CImg
#include <CImg.h>

using namespace cimg_library;
//using namespace DEM;
using namespace std;

int main (int argc, char ** argv)
{
    CImg<float> image("input.bmp");
    image.save("test.bmp");
}
```

When I tried to run, it appeared:

```
make all 
Linking CXX executable test1
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::cimg::X11_info::~X11_info()':
test1.cpp:(.text._ZN12cimg_library4cimg8X11_infoD2Ev[_ZN12cimg_library4cimg8X11_infoD5Ev]+0x2b): undefined reference to `XCloseDisplay'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::cimg::X11_attr()':
test1.cpp:(.text._ZN12cimg_library4cimg8X11_attrEv[_ZN12cimg_library4cimg8X11_attrEv]+0x70): undefined reference to `XInitThreads'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::flush()':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay5flushEv[_ZN12cimg_library11CImgDisplay5flushEv]+0x412): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay5flushEv[_ZN12cimg_library11CImgDisplay5flushEv]+0x4aa): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay5flushEv[_ZN12cimg_library11CImgDisplay5flushEv]+0x542): undefined reference to `XInitThreads'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::_handle_events(_XEvent const*)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0xa7): undefined reference to `XCheckWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x193): undefined reference to `XCheckWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x203): undefined reference to `XCheckWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x266): undefined reference to `XResizeWindow'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x2fb): undefined reference to `XCheckWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x36c): undefined reference to `XPutImage'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x38a): undefined reference to `XGetWindowAttributes'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x3a6): undefined reference to `XSync'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x3c6): undefined reference to `XSetInputFocus'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x3e3): undefined reference to `XCheckWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x433): undefined reference to `XCheckWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x4bb): undefined reference to `XCheckWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x5aa): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x67b): undefined reference to `XLookupString'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x6a4): undefined reference to `XQueryKeymap'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x6e8): undefined reference to `XLookupString'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent[_ZN12cimg_library11CImgDisplay14_handle_eventsEPK7_XEvent]+0x73d): undefined reference to `XUnmapWindow'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::_events_thread(void*)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_events_threadEPv[_ZN12cimg_library11CImgDisplay14_events_threadEPv]+0x44): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_events_threadEPv[_ZN12cimg_library11CImgDisplay14_events_threadEPv]+0x56): undefined reference to `XCheckTypedEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_events_threadEPv[_ZN12cimg_library11CImgDisplay14_events_threadEPv]+0x100): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_events_threadEPv[_ZN12cimg_library11CImgDisplay14_events_threadEPv]+0x154): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_events_threadEPv[_ZN12cimg_library11CImgDisplay14_events_threadEPv]+0x220): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_events_threadEPv[_ZN12cimg_library11CImgDisplay14_events_threadEPv]+0x2f0): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_events_threadEPv[_ZN12cimg_library11CImgDisplay14_events_threadEPv]+0x370): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay14_events_threadEPv[_ZN12cimg_library11CImgDisplay14_events_threadEPv]+0x3be): undefined reference to `XCheckMaskEvent'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::_set_colormap(unsigned long&, unsigned int)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay13_set_colormapERmj[_ZN12cimg_library11CImgDisplay13_set_colormapERmj]+0x111): undefined reference to `XStoreColors'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::_map_window()':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay11_map_windowEv[_ZN12cimg_library11CImgDisplay11_map_windowEv]+0x40): undefined reference to `XMapRaised'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay11_map_windowEv[_ZN12cimg_library11CImgDisplay11_map_windowEv]+0x72): undefined reference to `XWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay11_map_windowEv[_ZN12cimg_library11CImgDisplay11_map_windowEv]+0xb0): undefined reference to `XGetWindowAttributes'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay11_map_windowEv[_ZN12cimg_library11CImgDisplay11_map_windowEv]+0xf6): undefined reference to `XSync'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::assign()':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x33): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0xf1): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x168): undefined reference to `XDestroyWindow'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x1bd): undefined reference to `XSync'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x5e3): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x680): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x700): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x792): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x84c): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x8dd): undefined reference to `XInitThreads'
CMakeFiles/test1.dir/test1.cpp.o:test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x96e): more undefined references to `XInitThreads' follow
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::assign()':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x9bf): undefined reference to `XUngrabKeyboard'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0x9f2): undefined reference to `XFreeColormap'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[_ZN12cimg_library11CImgDisplay6assignEv]+0xa71): undefined reference to `XDestroyWindow'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay& cimg_library::CImgDisplay::render<unsigned int>(cimg_library::CImg<unsigned int> const&, bool)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6renderIjEERS0_RKNS_4CImgIT_EEb[_ZN12cimg_library11CImgDisplay6renderIjEERS0_RKNS_4CImgIT_EEb]+0x14f): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6renderIjEERS0_RKNS_4CImgIT_EEb[_ZN12cimg_library11CImgDisplay6renderIjEERS0_RKNS_4CImgIT_EEb]+0x50c): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6renderIjEERS0_RKNS_4CImgIT_EEb[_ZN12cimg_library11CImgDisplay6renderIjEERS0_RKNS_4CImgIT_EEb]+0x56a): undefined reference to `XInitThreads'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay& cimg_library::CImgDisplay::render<unsigned char>(cimg_library::CImg<unsigned char> const&, bool)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb[_ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb]+0x156): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb[_ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb]+0x6f1): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb[_ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb]+0x752): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb[_ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb]+0x2fd1): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb[_ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb]+0x62ef): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb[_ZN12cimg_library11CImgDisplay6renderIhEERS0_RKNS_4CImgIT_EEb]+0x637e): undefined reference to `XInitThreads'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay& cimg_library::CImgDisplay::assign<unsigned char>(cimg_library::CImg<unsigned char> const&, char const*, unsigned int, bool, bool)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignIhEERS0_RKNS_4CImgIT_EEPKcjbb[_ZN12cimg_library11CImgDisplay6assignIhEERS0_RKNS_4CImgIT_EEPKcjbb]+0x10a): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignIhEERS0_RKNS_4CImgIT_EEPKcjbb[_ZN12cimg_library11CImgDisplay6assignIhEERS0_RKNS_4CImgIT_EEPKcjbb]+0x121): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6assignIhEERS0_RKNS_4CImgIT_EEPKcjbb[_ZN12cimg_library11CImgDisplay6assignIhEERS0_RKNS_4CImgIT_EEPKcjbb]+0x2a6): undefined reference to `XSendEvent'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::screen_height()':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay13screen_heightEv[_ZN12cimg_library11CImgDisplay13screen_heightEv]+0x8e): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay13screen_heightEv[_ZN12cimg_library11CImgDisplay13screen_heightEv]+0xd3): undefined reference to `XOpenDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay13screen_heightEv[_ZN12cimg_library11CImgDisplay13screen_heightEv]+0xf5): undefined reference to `XCloseDisplay'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::screen_width()':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay12screen_widthEv[_ZN12cimg_library11CImgDisplay12screen_widthEv]+0x8e): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay12screen_widthEv[_ZN12cimg_library11CImgDisplay12screen_widthEv]+0xd3): undefined reference to `XOpenDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay12screen_widthEv[_ZN12cimg_library11CImgDisplay12screen_widthEv]+0xf5): undefined reference to `XCloseDisplay'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::_init_fullscreen()':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay16_init_fullscreenEv[_ZN12cimg_library11CImgDisplay16_init_fullscreenEv]+0x106): undefined reference to `XCreateWindow'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay16_init_fullscreenEv[_ZN12cimg_library11CImgDisplay16_init_fullscreenEv]+0x1a6): undefined reference to `XCreateImage'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay16_init_fullscreenEv[_ZN12cimg_library11CImgDisplay16_init_fullscreenEv]+0x1bd): undefined reference to `XSelectInput'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay16_init_fullscreenEv[_ZN12cimg_library11CImgDisplay16_init_fullscreenEv]+0x1cc): undefined reference to `XMapRaised'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay16_init_fullscreenEv[_ZN12cimg_library11CImgDisplay16_init_fullscreenEv]+0x1e8): undefined reference to `XWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay16_init_fullscreenEv[_ZN12cimg_library11CImgDisplay16_init_fullscreenEv]+0x239): undefined reference to `XPutImage'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay16_init_fullscreenEv[_ZN12cimg_library11CImgDisplay16_init_fullscreenEv]+0x250): undefined reference to `XGetWindowAttributes'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay16_init_fullscreenEv[_ZN12cimg_library11CImgDisplay16_init_fullscreenEv]+0x266): undefined reference to `XSync'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay16_init_fullscreenEv[_ZN12cimg_library11CImgDisplay16_init_fullscreenEv]+0x2ea): undefined reference to `XInitThreads'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::move(int, int)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0xa4): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0xc8): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0xf2): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x16e): undefined reference to `XSendEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x179): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x1aa): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x1be): undefined reference to `XMoveWindow'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x1da): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x204): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x280): undefined reference to `XSendEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x288): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x2d8): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay4moveEii[_ZN12cimg_library11CImgDisplay4moveEii]+0x390): undefined reference to `XInitThreads'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::_assign(unsigned int, unsigned int, char const*, unsigned int, bool, bool)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0xac): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x545): undefined reference to `XCreateWindow'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x560): undefined reference to `XSelectInput'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x583): undefined reference to `XStoreName'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x59a): undefined reference to `XAllocClassHint'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x5c2): undefined reference to `XSetClassHint'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x5ca): undefined reference to `XFree'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x672): undefined reference to `XCreateImage'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x68c): undefined reference to `XInternAtom'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x6a6): undefined reference to `XInternAtom'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x6cc): undefined reference to `XSetWMProtocols'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x721): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x862): undefined reference to `XGrabKeyboard'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x8b3): undefined reference to `XCreateSimpleWindow'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x8ed): undefined reference to `XMapRaised'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x91d): undefined reference to `XWindowEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x96e): undefined reference to `XGetWindowAttributes'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x99e): undefined reference to `XSync'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0x9e1): undefined reference to `XOpenDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0xb03): undefined reference to `XVisualIDFromVisual'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0xb21): undefined reference to `XGetVisualInfo'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0xb5b): undefined reference to `XFree'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0xb67): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0xbda): undefined reference to `XCreateColormap'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb[_ZN12cimg_library11CImgDisplay7_assignEjjPKcjbb]+0xc0f): undefined reference to `XSetWindowColormap'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay::resize(int, int, bool)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x172): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x275): undefined reference to `XResizeWindow'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x289): undefined reference to `XGetWindowAttributes'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x40a): undefined reference to `XCreateImage'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x42e): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x468): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x47f): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x5b9): undefined reference to `XSendEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x62d): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x650): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x681): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x729): undefined reference to `XSendEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x733): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x741): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x75c): undefined reference to `XMoveWindow'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x779): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x7a3): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x84b): undefined reference to `XSendEvent'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0x853): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0xa06): undefined reference to `XInitThreads'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay6resizeEiib[_ZN12cimg_library11CImgDisplay6resizeEiib]+0xa95): undefined reference to `XInitThreads'
CMakeFiles/test1.dir/test1.cpp.o: In function `cimg_library::CImgDisplay& cimg_library::CImgDisplay::display<unsigned char>(cimg_library::CImg<unsigned char> const&)':
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7displayIhEERS0_RKNS_4CImgIT_EE[_ZN12cimg_library11CImgDisplay7displayIhEERS0_RKNS_4CImgIT_EE]+0x7f): undefined reference to `XLockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7displayIhEERS0_RKNS_4CImgIT_EE[_ZN12cimg_library11CImgDisplay7displayIhEERS0_RKNS_4CImgIT_EE]+0xec): undefined reference to `XPutImage'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7displayIhEERS0_RKNS_4CImgIT_EE[_ZN12cimg_library11CImgDisplay7displayIhEERS0_RKNS_4CImgIT_EE]+0xf4): undefined reference to `XUnlockDisplay'
test1.cpp:(.text._ZN12cimg_library11CImgDisplay7displayIhEERS0_RKNS_4CImgIT_EE[_ZN12cimg_library11CImgDisplay7displayIhEERS0_RKNS_4CImgIT_EE]+0x15a): undefined reference to `XInitThreads'
collect2: error: ld returned 1 exit status
make[2]: *** [test/test1] Error 1
make[1]: *** [test/CMakeFiles/test1.dir/all] Error 2
make: *** [all] Error 2

16:16:51 Build Finished (took 217ms)

```

I think this is caused by cmake file, so i went there and added an inclusion to FindCImg.cmake, which is :

```
FIND_PATH(CIMG_INCLUDE_DIR CImg.h
      /usr/lib/CImg
      $ENV{HOME}/pkg/CImg
      /usr/include
      /usr/local/lib/CImg
      /opt/local/lib/CImg
      "${CMAKE_CURRENT_SOURCE_DIR}/CImg"
         )
SET(CIMG_FOUND 0)
IF(CIMG_INCLUDE_DIR)
    SET(CIMG_FOUND 1)
    SET(CIMG_INCLUDE_DIRS ${CIMG_INCLUDE_DIR})
ELSE(CIMG_INCLUDE_DIR)
    MESSAGE(FATAL ERROR "CImg.h not found - Please install CImg")
ENDIF(CIMG_INCLUDE_DIR)
```

Nothing changed. I found that the folder for CImg always is  /usr/include. No matter how I change the search option. I also tried external library:

```
#include "CImg.h"
```

But things are the same. Could anyone tell me something to try? Thanks a lot.

---

