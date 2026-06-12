---
title: "Compiling issue undefined reference to symbol 'clock_gettime@@GLIBC_2.2'"
date: 2012-05-23
forum: Programming Talk
---

### Post by nevixa on 2012-05-23
Hi,

When compiling my c/c++ program in Netbeans I get this error:
```
gcc -I/usr/local/include/opencv -I/usr/local/include -pthread -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/i386-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/i386-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0 -fpermissive    -L/usr/local/lib -lopencv_core -lopencv_imgproc -lopencv_highgui -lopencv_ml -lopencv_video -lopencv_features2d -lopencv_calib3d -lopencv_objdetect -lopencv_contrib -lopencv_legacy -lopencv_flann -ldecodeqr -L/usr/local/lib/ -lcurl -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0 -o dist/Debug/GNU-Linux-x86/trunk build/Debug/GNU-Linux-x86/cardObject.o build/Debug/GNU-Linux-x86/visualisation.o build/Debug/GNU-Linux-x86/monitoring.o build/Debug/GNU-Linux-x86/main.o build/Debug/GNU-Linux-x86/player.o build/Debug/GNU-Linux-x86/detectBiddings.o build/Debug/GNU-Linux-x86/gameStatsObject.o build/Debug/GNU-Linux-x86/cardOCR.o build/Debug/GNU-Linux-x86/cardModifications.o build/Debug/GNU-Linux-x86/geometry.o build/Debug/GNU-Linux-x86/boardNumber.o build/Debug/GNU-Linux-x86/cardSuit.o build/Debug/GNU-Linux-x86/bidObject.o build/Debug/GNU-Linux-x86/dummyCorner.o build/Debug/GNU-Linux-x86/trayCorner.o build/Debug/GNU-Linux-x86/logicConnection.o build/Debug/GNU-Linux-x86/bidSuit.o build/Debug/GNU-Linux-x86/bmCommunication.o build/Debug/GNU-Linux-x86/imageProcessing.o build/Debug/GNU-Linux-x86/bidOCR.o -lopencv_core -lopencv_highgui -lopencv_imgproc -lopencv_video -lclsocket -ldecodeqr 
/usr/bin/ld: build/Debug/GNU-Linux-x86/imageProcessing.o: undefined reference to symbol 'clock_gettime@@GLIBC_2.2'
/usr/bin/ld: note: 'clock_gettime@@GLIBC_2.2' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/librt.so so try adding it to the linker command line
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/librt.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/trunk] Error 1
make[2]: Leaving directory `/home/user/NetBeansProjects/bcr/trunk'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/user/NetBeansProjects/bcr/trunk'
make: *** [.build-impl] Error 2
```I'm on Ubuntu 12.04.  I have the same code running on Ubuntu 10.10 without any compiling problems. I assume there is a library linking problem, but I do not have a clue how to solve this. 

Thank you

---

### Post by roelforg on 2012-05-23
Move your sourcefiles to the begin of the command and put -lrt after the source files.
 
G++ can be a little picky about the order (i know why, but i don't feel like explaining it)

---

### Post by nevixa on 2012-05-23
Thank you roelforg. I made a mess of the included libraries, so I start with cleaning that up.

---

### Post by roelforg on 2012-05-23
> **nevixa said:**
> Thank you roelforg. I made a mess of the included libraries, so I start with cleaning that up.

If you don't mind the longer compile times, order like this:
```

-Wl,--start-group <source files and libraries go here, order not important> -Wl,--end-group

```
This'll cause the linker to keep researching the list until all references are resolved.

---

### Post by nevixa on 2012-05-23
Good tip, thanx.

---

### Post by nevixa on 2012-05-24
I cleaned out my code and tried to clean out  my includes. I'm trying to add libxml++-2.6 (version 2.35.2?) to my Netbeans program.

My includes  before adding libxml++-2.6:
```
-Wl,--start-group -I/usr/local/include/opencv -I/usr/local/include -pthread -Wl,--end-group -fpermissive
```Compiles perfectly. 
I added the output of** pkg-config libxml++-2.6 --cflags --libs**to my addition compiler options. Giving me:

```
gcc -Wl,--start-group -L/usr/local/lib -lopencv_core -lopencv_imgproc -lopencv_highgui -lopencv_ml -lopencv_video -lopencv_features2d -lopencv_calib3d -lopencv_objdetect -lopencv_contrib -lopencv_legacy -lopencv_flann -pthread -I/usr/local/include/libxml++-2.6 -I/usr/local/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/i386-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/i386-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -L/usr/local/lib -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0 -Wl,--end-group -o dist/Debug/GNU-Linux-x86/trunk build/Debug/GNU-Linux-x86/cardObject.o build/Debug/GNU-Linux-x86/visualisation.o build/Debug/GNU-Linux-x86/monitoring.o build/Debug/GNU-Linux-x86/main.o build/Debug/GNU-Linux-x86/player.o build/Debug/GNU-Linux-x86/detectBiddings.o build/Debug/GNU-Linux-x86/gameStatsObject.o build/Debug/GNU-Linux-x86/cardOCR.o build/Debug/GNU-Linux-x86/cardModifications.o build/Debug/GNU-Linux-x86/geometry.o build/Debug/GNU-Linux-x86/boardNumber.o build/Debug/GNU-Linux-x86/cardSuit.o build/Debug/GNU-Linux-x86/bidObject.o build/Debug/GNU-Linux-x86/dummyCorner.o build/Debug/GNU-Linux-x86/trayCorner.o build/Debug/GNU-Linux-x86/logicConnection.o build/Debug/GNU-Linux-x86/bidSuit.o build/Debug/GNU-Linux-x86/bmCommunication.o build/Debug/GNU-Linux-x86/imageProcessing.o build/Debug/GNU-Linux-x86/bidOCR.o -lclsocket -lopencv_core -lopencv_highgui -lopencv_imgproc -lopencv_legacy -lopencv_ml -lopencv_video -lcurl -lxml++-2.6 
/usr/bin/ld: build/Debug/GNU-Linux-x86/logicConnection.o: undefined reference to symbol 'Glib::ustring::compare(char const*) const'
/usr/bin/ld: note: 'Glib::ustring::compare(char const*) const' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libglibmm-2.4.so so try adding it to the linker command line
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libglibmm-2.4.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/trunk] Error 1
make[2]: Leaving directory `/home/user/NetBeansProjects/bcr/trunk'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/user/NetBeansProjects/bcr/trunk'
make: *** [.build-impl] Error 2
```Any ideas what I'm doing wrong?

---

### Post by roelforg on 2012-05-24
> **nevixa said:**
> I cleaned out my code and tried to clean out  my includes. I'm trying to add libxml++-2.6 (version 2.35.2?) to my Netbeans program.

My includes  before adding libxml++-2.6:
```
-Wl,--start-group -I/usr/local/include/opencv -I/usr/local/include -pthread -Wl,--end-group -fpermissive
```Compiles perfectly. 
I added the output of** pkg-config libxml++-2.6 --cflags --libs**to my addition compiler options. Giving me:

```
gcc -Wl,--start-group -L/usr/local/lib -lopencv_core -lopencv_imgproc -lopencv_highgui -lopencv_ml -lopencv_video -lopencv_features2d -lopencv_calib3d -lopencv_objdetect -lopencv_contrib -lopencv_legacy -lopencv_flann -pthread -I/usr/local/include/libxml++-2.6 -I/usr/local/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/i386-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/i386-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -L/usr/local/lib -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0 -Wl,--end-group -o dist/Debug/GNU-Linux-x86/trunk build/Debug/GNU-Linux-x86/cardObject.o build/Debug/GNU-Linux-x86/visualisation.o build/Debug/GNU-Linux-x86/monitoring.o build/Debug/GNU-Linux-x86/main.o build/Debug/GNU-Linux-x86/player.o build/Debug/GNU-Linux-x86/detectBiddings.o build/Debug/GNU-Linux-x86/gameStatsObject.o build/Debug/GNU-Linux-x86/cardOCR.o build/Debug/GNU-Linux-x86/cardModifications.o build/Debug/GNU-Linux-x86/geometry.o build/Debug/GNU-Linux-x86/boardNumber.o build/Debug/GNU-Linux-x86/cardSuit.o build/Debug/GNU-Linux-x86/bidObject.o build/Debug/GNU-Linux-x86/dummyCorner.o build/Debug/GNU-Linux-x86/trayCorner.o build/Debug/GNU-Linux-x86/logicConnection.o build/Debug/GNU-Linux-x86/bidSuit.o build/Debug/GNU-Linux-x86/bmCommunication.o build/Debug/GNU-Linux-x86/imageProcessing.o build/Debug/GNU-Linux-x86/bidOCR.o -lclsocket -lopencv_core -lopencv_highgui -lopencv_imgproc -lopencv_legacy -lopencv_ml -lopencv_video -lcurl -lxml++-2.6 
/usr/bin/ld: build/Debug/GNU-Linux-x86/logicConnection.o: undefined reference to symbol 'Glib::ustring::compare(char const*) const'
/usr/bin/ld: note: 'Glib::ustring::compare(char const*) const' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libglibmm-2.4.so so try adding it to the linker command line
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libglibmm-2.4.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/trunk] Error 1
make[2]: Leaving directory `/home/user/NetBeansProjects/bcr/trunk'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/user/NetBeansProjects/bcr/trunk'
make: *** [.build-impl] Error 2
```Any ideas what I'm doing wrong?

It's not the includes that you need to put in the -Wl,--start-group -Wl,--end-group
This command line is how you should've done it:
```
gcc -L/usr/local/lib -I/usr/local/include/libxml++-2.6 -I/usr/local/lib/libxml++-2.6/include  -I/usr/include/libxml2 -I/usr/include/glibmm-2.4  -I/usr/lib/i386-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0  -I/usr/lib/i386-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0  -I/usr/lib/i386-linux-gnu/glib-2.0/include -L/usr/local/lib  -Wl,--start-group -lopencv_core  -lopencv_imgproc -lopencv_highgui -lopencv_ml -lopencv_video  -lopencv_features2d -lopencv_calib3d -lopencv_objdetect -lopencv_contrib  -lopencv_legacy -lopencv_flann -pthread -lxml++-2.6  -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0 build/Debug/GNU-Linux-x86/cardObject.o  build/Debug/GNU-Linux-x86/visualisation.o  build/Debug/GNU-Linux-x86/monitoring.o build/Debug/GNU-Linux-x86/main.o  build/Debug/GNU-Linux-x86/player.o  build/Debug/GNU-Linux-x86/detectBiddings.o  build/Debug/GNU-Linux-x86/gameStatsObject.o  build/Debug/GNU-Linux-x86/cardOCR.o  build/Debug/GNU-Linux-x86/cardModifications.o  build/Debug/GNU-Linux-x86/geometry.o  build/Debug/GNU-Linux-x86/boardNumber.o  build/Debug/GNU-Linux-x86/cardSuit.o  build/Debug/GNU-Linux-x86/bidObject.o  build/Debug/GNU-Linux-x86/dummyCorner.o  build/Debug/GNU-Linux-x86/trayCorner.o  build/Debug/GNU-Linux-x86/logicConnection.o  build/Debug/GNU-Linux-x86/bidSuit.o  build/Debug/GNU-Linux-x86/bmCommunication.o  build/Debug/GNU-Linux-x86/imageProcessing.o  build/Debug/GNU-Linux-x86/bidOCR.o -lclsocket -lopencv_core  -lopencv_highgui -lopencv_imgproc -lopencv_legacy -lopencv_ml  -lopencv_video -lcurl -lxml++-2.6 -Wl,--end-group   -o dist/Debug/GNU-Linux-x86/trunk
```

---

### Post by MadCow108 on 2012-05-24
instead of messing around with groups, why not just do it right to begin with?
just move all -l... to the end of the line.

---

### Post by roelforg on 2012-05-24
> **MadCow108 said:**
> instead of messing around with groups, why not just do it right to begin with?
just move all -l... to the end of the line.

It's useful when you have circular dependencies (try using sdl with several of it's helper libs and you'll see how picky it is about where the source goes (hint: it's not at the end, or beginning but somewhere in the middle of the libs), then it's very useful to have groups).

---

### Post by nevixa on 2012-05-25
> **roelforg said:**
> It's not the includes that you need to put in the -Wl,--start-group -Wl,--end-group
This command line is how you should've done it:
```
gcc -L/usr/local/lib -I/usr/local/include/libxml++-2.6 -I/usr/local/lib/libxml++-2.6/include  -I/usr/include/libxml2 -I/usr/include/glibmm-2.4  -I/usr/lib/i386-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0  -I/usr/lib/i386-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0  -I/usr/lib/i386-linux-gnu/glib-2.0/include -L/usr/local/lib  -Wl,--start-group -lopencv_core  -lopencv_imgproc -lopencv_highgui -lopencv_ml -lopencv_video  -lopencv_features2d -lopencv_calib3d -lopencv_objdetect -lopencv_contrib  -lopencv_legacy -lopencv_flann -pthread -lxml++-2.6  -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0 build/Debug/GNU-Linux-x86/cardObject.o  build/Debug/GNU-Linux-x86/visualisation.o  build/Debug/GNU-Linux-x86/monitoring.o build/Debug/GNU-Linux-x86/main.o  build/Debug/GNU-Linux-x86/player.o  build/Debug/GNU-Linux-x86/detectBiddings.o  build/Debug/GNU-Linux-x86/gameStatsObject.o  build/Debug/GNU-Linux-x86/cardOCR.o  build/Debug/GNU-Linux-x86/cardModifications.o  build/Debug/GNU-Linux-x86/geometry.o  build/Debug/GNU-Linux-x86/boardNumber.o  build/Debug/GNU-Linux-x86/cardSuit.o  build/Debug/GNU-Linux-x86/bidObject.o  build/Debug/GNU-Linux-x86/dummyCorner.o  build/Debug/GNU-Linux-x86/trayCorner.o  build/Debug/GNU-Linux-x86/logicConnection.o  build/Debug/GNU-Linux-x86/bidSuit.o  build/Debug/GNU-Linux-x86/bmCommunication.o  build/Debug/GNU-Linux-x86/imageProcessing.o  build/Debug/GNU-Linux-x86/bidOCR.o -lclsocket -lopencv_core  -lopencv_highgui -lopencv_imgproc -lopencv_legacy -lopencv_ml  -lopencv_video -lcurl -lxml++-2.6 -Wl,--end-group   -o dist/Debug/GNU-Linux-x86/trunk
```

When I compile in terminal with the command line above I still get the Glib::ustring compile error:
```

/usr/bin/ld: build/Debug/GNU-Linux-x86/logicConnection.o: undefined reference to symbol 'Glib::ustring::compare(char const*) const'
/usr/bin/ld: note: 'Glib::ustring::compare(char const*) const' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libglibmm-2.4.so so try adding it to the linker command line
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libglibmm-2.4.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
```@MadCow108 thank you for your reaction. Do you mean like this:
```
gcc -L/usr/local/lib -I/usr/local/include/libxml++-2.6 -I/usr/local/lib/libxml++-2.6/include  -I/usr/include/libxml2 -I/usr/include/glibmm-2.4  -I/usr/lib/i386-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0  -I/usr/lib/i386-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0  -I/usr/lib/i386-linux-gnu/glib-2.0/include -L/usr/local/lib   build/Debug/GNU-Linux-x86/cardObject.o  build/Debug/GNU-Linux-x86/visualisation.o  build/Debug/GNU-Linux-x86/monitoring.o build/Debug/GNU-Linux-x86/main.o  build/Debug/GNU-Linux-x86/player.o  build/Debug/GNU-Linux-x86/detectBiddings.o  build/Debug/GNU-Linux-x86/gameStatsObject.o  build/Debug/GNU-Linux-x86/cardOCR.o  build/Debug/GNU-Linux-x86/cardModifications.o  build/Debug/GNU-Linux-x86/geometry.o  build/Debug/GNU-Linux-x86/boardNumber.o  build/Debug/GNU-Linux-x86/cardSuit.o  build/Debug/GNU-Linux-x86/bidObject.o  build/Debug/GNU-Linux-x86/dummyCorner.o  build/Debug/GNU-Linux-x86/trayCorner.o  build/Debug/GNU-Linux-x86/logicConnection.o  build/Debug/GNU-Linux-x86/bidSuit.o  build/Debug/GNU-Linux-x86/bmCommunication.o  build/Debug/GNU-Linux-x86/imageProcessing.o  build/Debug/GNU-Linux-x86/bidOCR.o -lclsocket -lopencv_core  -lopencv_highgui -lopencv_imgproc -lopencv_legacy -lopencv_ml  -lopencv_video -lcurl -lxml++-2.6 -pthread -lxml++-2.6  -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  -o dist/Debug/GNU-Linux-x86/trunk
```That seems actually to compile without errors! Now I am going to figure out how to get this compiled within netbeans. Thanks again!

---

### Post by nevixa on 2012-05-30
I finally figured out the problem in Netbeans. If you include the libraries in Netbeans there is no need to add all the -l... files manually. Removing the -l... files from the Addition Linker Options line fixed the problem for me.

---

