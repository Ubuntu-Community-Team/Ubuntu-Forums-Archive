---
title: "Undefined references (Like XFree..) After update to 11.10"
date: 2011-10-08
forum: Programming Talk
---

### Post by serengeor on 2011-10-08
So I udpated my ubuntu from (10.04) to 11.10. And I try to compile the project I was working on in 10.04. And then I get lots of undefined references :confused:
```
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/lib/Linux/libIrrlicht.a(CIrrDeviceLinux.o)||In function `~CIrrDeviceLinux':|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|136|undefined reference to `XFree'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|150|undefined reference to `glXMakeContextCurrent'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|155|undefined reference to `glXMakeCurrent'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|158|undefined reference to `glXDestroyContext'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|160|undefined reference to `glXDestroyWindow'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|172|undefined reference to `XDestroyWindow'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|173|undefined reference to `XCloseDisplay'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|177|undefined reference to `XFree'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|136|undefined reference to `XFree'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|150|undefined reference to `glXMakeContextCurrent'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|155|undefined reference to `glXMakeCurrent'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|158|undefined reference to `glXDestroyContext'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|160|undefined reference to `glXDestroyWindow'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|172|undefined reference to `XDestroyWindow'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|173|undefined reference to `XCloseDisplay'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|177|undefined reference to `XFree'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/lib/Linux/libIrrlicht.a(CIrrDeviceLinux.o)||In function `irr::IrrPrintXError(_XDisplay*, XErrorEvent*)':|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|200|undefined reference to `XGetErrorDatabaseText'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|201|undefined reference to `XGetErrorText'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/lib/Linux/libIrrlicht.a(CIrrDeviceLinux.o)||In function `irr::CIrrDeviceLinux::switchToFullscreen(bool)':|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|225|undefined reference to `XRRGetScreenInfo'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|226|undefined reference to `XRRSetScreenConfig'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|227|undefined reference to `XRRFreeScreenConfigInfo'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|281|undefined reference to `XRRQueryExtension'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|284|undefined reference to `XRRGetScreenInfo'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|285|undefined reference to `XRRConfigSizes'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|303|undefined reference to `XRRSetScreenConfig'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|306|undefined reference to `XRRFreeScreenConfigInfo'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/lib/Linux/libIrrlicht.a(CIrrDeviceLinux.o)||In function `irr::CIrrDeviceLinux::createWindow()':|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|355|undefined reference to `XSetErrorHandler'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|358|undefined reference to `XOpenDisplay'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|362|undefined reference to `XDisplayName'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|363|undefined reference to `XDisplayName'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|380|undefined reference to `glXQueryExtension'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|381|undefined reference to `glXQueryVersion'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|387|undefined reference to `glXGetProcAddress'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|535|undefined reference to `XFree'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|539|undefined reference to `glXGetProcAddress'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|573|undefined reference to `glXChooseVisual'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|581|undefined reference to `glXChooseVisual'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|587|undefined reference to `glXChooseVisual'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|612|undefined reference to `XGetVisualInfo'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|620|undefined reference to `XCloseDisplay'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|633|undefined reference to `XCreateColormap'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|653|undefined reference to `XCreateWindow'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|654|undefined reference to `XMapRaised'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|657|undefined reference to `XInternAtom'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|658|undefined reference to `XSetWMProtocols'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|661|undefined reference to `XSetInputFocus'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|663|undefined reference to `XGrabKeyboard'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|666|undefined reference to `XGrabPointer'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|668|undefined reference to `XWarpPointer'|
/home/ernestas/Ernesto/Programming/Libraries/irrlicht/source/Irrlicht/CIrrDeviceLinux.cpp|682|undefined reference to `XCreateWindow'|
||More errors follow but not being shown.|
||Edit the max errors limit in compiler options...|
||=== Build finished: 50 errors, 0 warnings (0 minutes, 23 seconds) ===|

```

I don't really get why it happens since I'm linking everything as usual "-lGL -lGLU -lXrandr -lXext -lX11" in codeblocks.

I'd like to know what could be causing problems here.

---

### Post by MadCow108 on 2011-10-08
the linker has a different behavior in 11.10
it by default uses the  --no-copy-dt-needed and--as-needed flags.
If you are linking against everything needed (required by --no-copy-dt-needed) make sure "-lGL -lGLU -lXrandr -lXext -lX11" is placed behind the objects needing their symbols on the commandline.
e.g.:
```
#right, symbols in file.c are registered as needed and provided by the following libraries
gcc file.c -lGL -lGLU -lXrandr -lXext -lX11
#wrong, the linker will think the libraries are not needed and will drop them
gcc -lGL -lGLU -lXrandr -lXext -lX11 file.c
```

the behavior can be disabled with -Wl,--no-as-needed in gcc


A common mistake which causes this issue when using autotools is placing libraries in the LDFLAGS variable, that is intended for linker flags not libraries to link with. Those should go into LIBS, LDADD or LIBADD

---

### Post by serengeor on 2011-10-08
Thanks for explaining, I'll try that ASAP and report back :popcorn:

> 
A common mistake which causes this issue when using autotools is placing libraries in the LDFLAGS variable, that is intended for linker flags not libraries to link with. Those should go into LIBS, LDADD or LIBADD

Yes, a common mistake.. :D
Thanks for the tip it's fixed now :)

---

