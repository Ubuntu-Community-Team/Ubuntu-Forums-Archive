---
title: "Compiling Gambatte; (ossengine) ‘perror’ was not declared in this scope"
date: 2010-08-16
forum: Packaging and Compiling Programs
---

### Post by NightwishFan on 2010-08-16
Hello and thanks in advance for taking a look at my problem. I was interested in compiling and Debianizing the emulator Gambatte for my own personal use as it is seems far superior to VisualboyAdvance.

This is my first time Debianizing, but not my first time compiling. I hit a snag compiling with this as the output:

```

g++ -c -pipe -fno-exceptions -fno-rtti -O2 -Wall -W -D_REENTRANT -DHAVE_STDINT_H -DPLATFORM_UNIX -DQT_NO_DEBUG -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4 -Iframework/SDL_Joystick/include -I../../common -I../../libgambatte/include -I/usr/X11R6/include -I. -o ossengine.o framework/audioengines/ossengine.cpp
framework/audioengines/ossengine.cpp: In member function ‘virtual int OssEngine::doInit(int, unsigned int)’:
framework/audioengines/ossengine.cpp:43: error: ‘perror’ was not declared in this scope
framework/audioengines/ossengine.cpp:51: error: ‘perror’ was not declared in this scope
framework/audioengines/ossengine.cpp:56: error: ‘printf’ was not declared in this scope
framework/audioengines/ossengine.cpp:65: error: ‘perror’ was not declared in this scope
framework/audioengines/ossengine.cpp:70: error: ‘printf’ was not declared in this scope
framework/audioengines/ossengine.cpp:76: error: ‘perror’ was not declared in this scope
framework/audioengines/ossengine.cpp:87: error: ‘perror’ was not declared in this scope
framework/audioengines/ossengine.cpp:96: error: ‘perror’ was not declared in this scope
make[1]: *** [ossengine.o] Error 1
make[1]: Leaving directory `/dev/shm/Build/gambatte-0.4.1/gambatte_qt/src'
make: *** [sub-src-make_default] Error 2

```

I assumed I am missing some headers for OSS or etc, however it seems I have them. Can anyone aid me, I am making this a bit of a project to teach me more about Debian/Ubuntu and compiling software.

---

### Post by SevenMachines on 2010-08-16
Starting with gcc 4.3 there was a clean up of dependencies which means that some code needs to explicitly add includes to use >4.3 versions. if i remember right i think perror and printf are the result of a missing
> #include <cstdio>you'll need to use whatever patch system you're using to create a patch to allow compilation on newer gcc's.
theres a list of some of the common errors and needed includes on upgrading to gcc 4.3 and above [here]("http://gcc.gnu.org/gcc-4.3/porting_to.html")

---

