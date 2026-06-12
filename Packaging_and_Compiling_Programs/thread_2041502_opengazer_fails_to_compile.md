---
title: "opengazer fails to compile"
date: 2012-08-12
forum: Packaging and Compiling Programs
---

### Post by dstaubsauger on 2012-08-12
Hi Everyone!

I'm trying to compile [opengazer]("http://www.inference.phy.cam.ac.uk/opengazer/"), a tool that tracks your eye movement and can be used together with [Dasher]("http://www.inference.phy.cam.ac.uk/dasher/") to provide an eyes-only method of entering text. I'm running Ubuntu 12.04 Precise Pangolin.

*[SIZE="1"](The following part describes what i did up to the point until the error occurred and might be somewhat unrelated to my problem. If you want, skip to the interesting part at the smiley with the popcorn.)[/SIZE]*

So, i downloaded [the source]("http://www.inference.phy.cam.ac.uk/opengazer/opengazer-0.1.2.tar.gz") (v 0.1.2), unpacked it and read the README. I installed all the dependencies listed there from the Ubuntu repos and modified the Makefile as instructed, changing the line ```
VXLDIR = /opt
``` to ```
VXLDIR = /usr
``` because this is where Ubuntu installs vxl.

Next, i attempted to compile opengazer by running *make*, but it failed with the error```
$ make
g++ -c -Wall -g -O3 -o opengazer.o `pkg-config cairomm-1.0 opencv gtkmm-2.4 --cflags`  -I/usr/local/include/core -I/usr/local/include/vcl -I/usr/local/include/contrib/oxl  -I/usr/include/core -I/usr/include/vcl -I/usr/include/contrib/oxl  -I/usr/include/vxl/core -I/usr/include/vxl/vcl -I/usr/include/vxl/contrib/oxl opengazer.cpp 
In file included from TrackingSystem.h:3:0,
                 from MainGazeTracker.h:3,
                 from GazeArea.h:3,
                 from GazeTrackerGtk.h:6,
                 from opengazer.cpp:3:
PointTracker.h:11:33: error: reference to 'exception' is ambiguous
/usr/include/boost/exception/exception.hpp:193:5: error: candidates are: class boost::exception
/usr/include/c++/4.6/exception:61:9: error:                 class std::exception
make: *** [opengazer.o] Error 1

```I fixed this one with the help of another forum i found on google, where someone suggested to change the line ```
class TrackingException: public exception {};
``` to ```
class TrackingException: public std::exception {};

``` in *PointTracker.h* to clean up the ambiguity between the std exception and the boost exception. I did that and the file compiled.

:popcorn:
Then I ran *make* again and got the error that I'm currently stuck with. There is a whole bunch of error messages, with the first ones being ```
g++ -Wall -g -O3 -o opengazer `pkg-config cairomm-1.0 opencv gtkmm-2.4 --libs`  -L/usr/lib -L/usr/local/lib -lm -ldl -lvnl -lmvl -lvnl_algo -lvgl -lgthread-2.0  opengazer.o Calibrator.o GazeTrackerGtk.o HeadTracker.o LeastSquares.o EyeExtractor.o GazeTracker.o MainGazeTracker.o OutputMethods.o PointTracker.o FaceDetector.o GazeArea.o TrackingSystem.o GtkStore.o Containers.o GraphicalPointer.o Point.o utils.o BlinkDetector.o FeatureDetector.o Alert.o
Calibrator.o: In function `__static_initialization_and_destruction_0':
/usr/include/gtkmm-2.4/gtkmm/papersize.h:41: undefined reference to `Glib::ustring::ustring(char const*)'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:41: undefined reference to `Glib::ustring::~ustring()'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:42: undefined reference to `Glib::ustring::ustring(char const*)'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:42: undefined reference to `Glib::ustring::~ustring()'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:43: undefined reference to `Glib::ustring::ustring(char const*)'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:43: undefined reference to `Glib::ustring::~ustring()'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:44: undefined reference to `Glib::ustring::ustring(char const*)'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:44: undefined reference to `Glib::ustring::~ustring()'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:45: undefined reference to `Glib::ustring::ustring(char const*)'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:45: undefined reference to `Glib::ustring::~ustring()'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:46: undefined reference to `Glib::ustring::ustring(char const*)'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:46: undefined reference to `Glib::ustring::~ustring()'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:47: undefined reference to `Glib::ustring::ustring(char const*)'
/usr/include/gtkmm-2.4/gtkmm/papersize.h:47: undefined reference to `Glib::ustring::~ustring()'

``` I have attached a complete log of these errors and those occuring afterwards (I'm not sure whether the others are consecutive errors caused by the first ones).
libgtkmm-2.4-dev and libglib2.0-dev are installed on my system. I found forum threads about similar compile errors with papersize.h with Google, but none of them is related to opengazer:

[http://www.eclipse.org/forums/index.php/m/873552/]("http://www.eclipse.org/forums/index.php/m/873552/")
[https://mail.gnome.org/archives/gtkmm-list/2008-June/msg00017.html]("https://mail.gnome.org/archives/gtkmm-list/2008-June/msg00017.html")
[http://forums.codeblocks.org/index.php?topic=14142.0]("http://forums.codeblocks.org/index.php?topic=14142.0")

Unfortunately, I'm not a C/C++ developer and can't make much sense of those discussions. I have attached my modified *Makefile* and (the probably somewhat unrelated) *PointTracker.h* as well as the error log i mentioned. Please tell me if I need to provide further information on my system/installed packages/whatever.

Any help on how to get this program compile and run is appreciated! :)

---

### Post by SevenMachines on 2012-08-14
The object files need to come before the linker libraries, probably change the Makefile

```
opengazer: 	$(objects)
	g++ $(CPPFLAGS) -o $@ `pkg-config cairomm-1.0 opencv gtkmm-2.4 --libs`  $(LINKER) $^
```

to
```
opengazer:  $(objects)
  g++ $(CPPFLAGS) -o $@ $^ `pkg-config cairomm-1.0 opencv gtkmm-2.4 --libs`  $(LINKER)
```

---

### Post by dstaubsauger on 2012-08-14
Thank you!

(If anyone wants to use SevenMachines's fix, make sure the second line starts with a tab and not spaces)

However, the *./opengazer* i get segfaults immeadetly after startup. I'd like to take a closer look at that, but unfortunately i don't know how to turn off the gcc optimizations that cause the lack of debug information: ```
Reading symbols from /home/me/opengazer/opengazer-0.1.2/opengazer...done.
(gdb) r
Starting program: /home/me/opengazer/opengazer-0.1.2/opengazer 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Program received signal SIGSEGV, Segmentation fault.
MainGazeTracker::MainGazeTracker (this=0x7fffffffe010, argc=1, argv=0x7fffffffe1c8, stores=...) at MainGazeTracker.cpp:67
67		videoinput.reset(new VideoInput());
(gdb) bt
#0  MainGazeTracker::MainGazeTracker (this=0x7fffffffe010, argc=1, argv=0x7fffffffe1c8, stores=...) at MainGazeTracker.cpp:67
#1  0x0000000000420379 in GazeArea::GazeArea (this=0x7fffffffdff0, argc=1, argv=0x7fffffffe1c8, stores=..., __in_chrg=<optimized out>, 
    __vtt_parm=<optimized out>) at GazeArea.cpp:7
#2  0x000000000040cf17 in GazeTrackerGtk::GazeTrackerGtk (this=0x7fffffffde30, argc=1, argv=0x7fffffffe1c8, __in_chrg=<optimized out>, 
    __vtt_parm=<optimized out>) at GazeTrackerGtk.cpp:23
#3  0x0000000000409a66 in main (argc=1, argv=0x7fffffffe1c8) at opengazer.cpp:15
(gdb) k
Kill the program being debugged? (y or n) y
(gdb) q

``` What do i need to do to the Makefile to get a more verbose backtrace?

---

### Post by SevenMachines on 2012-08-14
-g and -O0 are the options to g++ you'll want to try

---

### Post by SevenMachines on 2012-08-14
And you may or may not want 'backtrace full' too

---

### Post by dstaubsauger on 2012-08-16
Thanks, that produces a lot of ... output :P

Please remind me to come get back to this when i know what i'm doing ^^

---

