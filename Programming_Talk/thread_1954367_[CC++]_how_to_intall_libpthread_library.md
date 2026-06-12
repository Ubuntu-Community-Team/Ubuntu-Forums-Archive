---
title: "[C/C++] how to intall libpthread library?"
date: 2012-04-07
forum: Programming Talk
---

### Post by josephellengar on 2012-04-07
Hi. I wrote a program using pthreads in c++/Ubuntu, but when I try to compile it the linker is complaining about undefined references to pthread_create. What package do I need to have installed to use this, and also where would I find the library to link it up to compile in codeblocks?

Thank you!

---

### Post by Bachstelze on 2012-04-08
Most probably wrong flag ordering. Post your command with the exact error.

---

### Post by Zugzwang on 2012-04-08
I would say that the common cause for this error is forgetting to link against pthread.

Here is what a quick google search found for me: [http://gabrielshen.blogspot.de/2008/06/how-to-run-pthread-in-codeblocks.html](http://gabrielshen.blogspot.de/2008/06/how-to-run-pthread-in-codeblocks.html)

---

### Post by josephellengar on 2012-04-08
Never mind, I had put the -lpthread command in the wrong place. I had it in compiler options instead of linker options. d'oh. By the way, love your username, Zugzwang. Thanks!

---

### Post by tal111 on 2012-04-08
I follow this instructions 
**Adding -pthread to eclipse, for using posix threads**

[http://blog.asteriosk.gr/2009/02/15/adding-pthread-to-eclipse-for-using-posix-threads/](http://blog.asteriosk.gr/2009/02/15/adding-pthread-to-eclipse-for-using-posix-threads/)
and I am still getting this error :**_gcc-pthread: not found_**

make all 
Building target: robot2.exe
Invoking: GCC C Linker
gcc`pkg-config --cflags --libs gtk+-2.0  opencv libglade-2.0 glib-2.0 gthread-2.0 `-L/usr/lib/x86_64-linux-gnu/pkgconfig -o "robot2.exe"  ./src/test_listener/TestListenerThread.o  ./src/sensor_thread/SensorThread.o  ./src/main/main.o  ./src/image_thread/ImageThead.o  ./src/gui/gui.o  ./src/event_thread/EventThread.o  ./src/common/Msg.o   -lpthread
/bin/sh:**_ gcc-pthread: not found_**
make: *** [robot2.exe] Error 127

---

### Post by tal111 on 2012-04-10
to add at the linker command  -Wl,-no-as-needed before the pkg-config solve the problem :
${COMMAND} -Wl,-no-as-needed ` pkg-config --cflags --libs gtk+-2.0  opencv libglade-2.0 ` ${FLAGS} ${OUTPUT_FLAG} ${OUTPUT_PREFIX}${OUTPUT} ${INPUTS}

---

