---
title: "[SOLVED] kde/qt libs in ubuntu?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by stevek123 on 2008-09-17
I was trying to install an app, GraphCalc, for my kids to do math homework (cant afford to buy a graph calc right now...). I was able to make & install the peripherals it asked for but the final 'qmake' was a failure. I'm running Hardy and installed the qt3 & qt4 libs thru synaptic. Seems these qt libs are insufficient for the app. I'm too much of a noob (and very gui oriented) to understand which other kde libs I would need. Is this even 'do-able' without a full kde install? FWIW, commands that failed included qvaraiant.h , qpixmap.h, qmainwindow.h, qapplication.h...:confused: Any help/direction appreciated.
Steve

---

### Post by ggaaron on 2008-09-17
If you have to compile it from source, you'll need '-dev' packages. Probably qt-dev or something.

---

### Post by OffAxis on 2008-09-17
try libqt3-headers

```
sudo apt-get install libqt3-headers
```

Here's the listing:
[http://packages.ubuntu.com/hardy/i386/libqt3-headers/filelist](http://packages.ubuntu.com/hardy/i386/libqt3-headers/filelist)

> Is this even 'do-able' without a full kde install? 

absolutely.

---

### Post by NewJack on 2008-09-17
You can still run KDE apps in GNOME.  I use K3B for ripping CDs, burning DVDs, etc with no problems in GNOME.  GraphCalc should work with the right dependencies installed.

---

### Post by stevek123 on 2008-09-17
so far I added qt3-dev-tools but need more i guess. several options in synaptic when i search for qt-dev but they dont look like they are what i need. Not sure how to refine my search to show the apps I really need :p
Steve

---

### Post by NewJack on 2008-09-17
Steve,
  Here is the support email address for GraphCalc: 

[email]support@graphcalc.com[/email]

Maybe they will advise the steps needed to get it running under GNOME.

Joe

---

### Post by stevek123 on 2008-09-17
I added the 'qt headers' and tried a qmake & make but still failed. Reviewed the 'headers' info during install. It shows a number of pkgs I need to remove. I'll try and follow thru with that and retry. will post later with update and probably more ?s. 
Thanks to all for quick replies!
Steve

---

### Post by alienexplorers on 2008-09-17
Have you tried the gnome graphing calculator > extcalc which is found in the repositories.

---

### Post by ggaaron on 2008-09-17
To build anything from source you need build-essential and dev packages for libraries that you depend on to provide headers, you have to look at the error itself and install a good package.
I'm afraid that I can't help you more than this as partially for this reason (difficulty in making own packages) I don't use binary distributions...

---

### Post by nowshining on 2008-09-17
did you try looking into the repos?? did you look online for already compiled, debs, rpms, etc.. u can use alien to convert rpms to deb. :) sudo apt-get install alien fakeroot

sudo fakeroot alien -d name/pathtofile

where is this graph calc anyway?? ie: link, etc..

---

### Post by stevek123 on 2008-09-17
> **nowshining said:**
> 

where is this graph calc anyway?? ie: link, etc..

[http://www.graphcalc.com/download.shtml](http://www.graphcalc.com/download.shtml)

---

### Post by stevek123 on 2008-09-18
I had loaded all the qt4 files incl the -dev files but it looks like i needed the qt3 files in full also. I installed libqt3-mt-dev, reran qmake, reran make. It started up pretty well and was putting it together for about 4 minutes, but ended up failing at this point...

g++  -o graphcalc .obj/main.o .obj/expression.o .obj/graph2d.o .obj/graph3d.o .obj/mainform.o .obj/about.o .obj/graph2doptions.o .obj/graph3doptions.o .obj/graph3drendermodes.o .obj/outputmode.o .obj/qmake_image_collection.o .obj/moc_graph3d.o .obj/moc_mainform.o .obj/moc_about.o .obj/moc_graph2doptions.o .obj/moc_graph3doptions.o .obj/moc_graph3drendermodes.o .obj/moc_outputmode.o   -L/usr/share/qt3/lib -L/usr/X11R6/lib -L/usr/lib -L/usr/kde/3.1/lib -lginac -lcln -lgmp -lqt-mt -lXext -lX11 -lm -lpthread
/usr/bin/ld: cannot find -lgmp
collect2: ld returned 1 exit status
make: *** [graphcalc] Error 1

I'm a noob and not familiar with the -lgmp suffix = ???. Error 1 = ??? (other than the obvious failure). What else have I missed in my installation????

---

### Post by nowshining on 2008-09-18
If you get it compiled let me have a copy..

as for ur problem now - do

sudo apt-get install libmath-bigint-gmp-perl

and re-run make :) no need to make clean it should run thru just fine where it last errored...

---

### Post by stevek123 on 2008-09-18
> **nowshining said:**
> If you get it compiled let me have a copy..

as for ur problem now - do

sudo apt-get install libmath-bigint-gmp-perl

and re-run make :) no need to make clean it should run thru just fine where it last errored...

As for a copy... sure IF 1) I ever get it right & 2) you tell me how i do that??? (I'm really a noob! - but figure if I never try and learn this stuff I'll get nowhere with computers and remain stuck with the larger competitors) - but we'll work on that later...
I installed the lib and re-ran make. It continued right from where it stopped and stopped again at the same point with same error msg.

---

### Post by stevek123 on 2008-09-18
I went and googled gmp. It is an arithmatic library. One of the users of this lib is listed as CLN. This is one of the required parts to setup the graphcalc. I thought i had this configured, made, and installed properly. RATS! I paid attention while it was compiling but it took a LONG time (maybe 30 min) and I guess my attention strayed because i didnt catch any error messages. I even ran make check when I was done... hmmm...Where do I go to look at the log of this CLN make? Maybe I missed something there...

---

### Post by stevek123 on 2008-09-18
OK...latest update. I found and reviewed the CLN config log. Not really sure what the errors listed are/mean. so... I re-ran ./config since I've updated a couple of apps on the comp trying to get this right. It looks like it wants/looks for the fortran77 compiler but ends up working around it BUT gives me a WARNING that my gmp.h is too old to be used. It looks like I need to update my gmp (I thought I had!) and try again. 

My concern at this point is that I am going to miss a step by just re-running the config and make commands. I am unfamiliar (yet ;) ) with command line requirements - will I need to do something else before I run config or make... ?make clean?    If there is something I need to do like this please help. Thanks for your time in attention.
Steve

---

### Post by nowshining on 2008-09-18
a warning is just that a warning, it should work fine unless you get errored out...
make clean cleans up the files and undos the make part, if u want you could just

remove the folder grapchcal, re-untar the graphcalc folder and re-go into the linux part and re-./configure, etc...

and as the readme says it should create a script in the linux folder..... or basically a binary, then u should be able to move that binary or bin to /usr/bin and set a manual menu, etc.. from there, etc...

again try and see what happens, there is nothing to be converted about...alas don'e run make a root tho...

---

### Post by stevek123 on 2008-09-19
LOL ... I installed gmp3 -dev and -c++ files, re-made CLN. Went in perfect (almost an hour on my old dog comp!). Because this was listed as a primary routine for graphcalc, I ran make clean on graphcalc and then make. Started great and blew past my last error/fail point... but hit a NEW ONE.... something in 'graph3D' , wherever the heck that is from. End of error stream shows like this....

(a whole bunch of these.....)
graph3d.cpp:(.text+0xd6b): undefined reference to `glBegin'
graph3d.cpp:(.text+0xd7d): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xde6): undefined reference to `glVertex3d'
graph3d.cpp:(.text+0xdfa): undefined reference to `glEnd'
graph3d.cpp:(.text+0xe2d): undefined reference to `glEndList'
.obj/graph3d.o: In function `graph3d::resizeGL(int, int)':
graph3d.cpp:(.text+0x3ef): undefined reference to `glMatrixMode'
collect2: ld returned 1 exit status
make: *** [graphcalc] Error 1

:~$ ./graphcalc
bash: ./graphcalc: No such file or directory


Next step is to read the extra documentation... I'll update later.
(any suggestions???)

---

### Post by ggaaron on 2008-09-19
Quick guess - now you need opengl header files.

---

### Post by stevek123 on 2008-09-20
I've found out that graphcalc doesnt support this anymore...they send support to sorceforge. This is an old project and has little support or info there either.... but I did find this there...

"2. qmake is probably setting the wrong kde includes & libs 
(unless you're really using 3.1)
3. qmake most likely won't have set the right library flags 
for gl.

To fix 2 and 3, open the Makefile and change -I/usr/kde/3.1/
include on the INCPATH line to 3.x where x is your kde 
version. Do the same for LIBS Then add -lglut -lGLU -lGL to 
the LIBS variable as well. It should then compile."

It looks like my kde/qt is still not going to be what they are looking for. I guess thats my next step. I'll update later.

---

### Post by nowshining on 2008-09-21
> **stevek123 said:**
> I've found out that graphcalc doesnt support this anymore...they send support to sorceforge. This is an old project and has little support or info there either.... but I did find this there...

"2. qmake is probably setting the wrong kde includes & libs 
(unless you're really using 3.1)
3. qmake most likely won't have set the right library flags 
for gl.

To fix 2 and 3, open the Makefile and change -I/usr/kde/3.1/
include on the INCPATH line to 3.x where x is your kde 
version. Do the same for LIBS Then add -lglut -lGLU -lGL to 
the LIBS variable as well. It should then compile."

It looks like my kde/qt is still not going to be what they are looking for. I guess thats my next step. I'll update later.

okay i got it to almost compile do this:

change that /usr/kde to /usr/include/kde and do sudo apt-get install libginac-dev and it should / maybe compile fine on ur end when u run make but i get an error that I have to lookup why i say it maywork on ur end: my error is and i've had this error before and forgot how to fix it..

"/usr/bin/ld: cannot find -lgmp"

edit:okay  i'm going to see if libgmp-ocaml-dev or any libgmp in there will work...and of course fix this error...

---

### Post by nowshining on 2008-09-21
okay now it gives the following at around the end :/
```

.obj/graph3d.o: In function `graph3d::zoomStandard()':
graph3d.cpp:(.text+0x2e1): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x2fb): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x315): undefined reference to `glRotatef'
.obj/graph3d.o: In function `graph3d::resizeGL(int, int)':
graph3d.cpp:(.text+0x391): undefined reference to `glViewport'
graph3d.cpp:(.text+0x39d): undefined reference to `glMatrixMode'
graph3d.cpp:(.text+0x3a2): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x3e2): undefined reference to `glFrustum'
.obj/graph3d.o: In function `graph3d::initializeGL()':
graph3d.cpp:(.text+0x42e): undefined reference to `glMatrixMode'
graph3d.cpp:(.text+0x433): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x43f): undefined reference to `glMatrixMode'
graph3d.cpp:(.text+0x444): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x450): undefined reference to `glDrawBuffer'
graph3d.cpp:(.text+0x45c): undefined reference to `glEnable'
graph3d.cpp:(.text+0x468): undefined reference to `glShadeModel'
graph3d.cpp:(.text+0x47c): undefined reference to `glClearDepth'
.obj/graph3d.o: In function `graph3d::paintGL()':
graph3d.cpp:(.text+0x857): undefined reference to `glClear'
graph3d.cpp:(.text+0x863): undefined reference to `glClear'
graph3d.cpp:(.text+0x880): undefined reference to `glClearColor'
graph3d.cpp:(.text+0x88c): undefined reference to `glClear'
graph3d.cpp:(.text+0x8a0): undefined reference to `glPolygonMode'
graph3d.cpp:(.text+0x8a5): undefined reference to `glPushMatrix'
graph3d.cpp:(.text+0x8aa): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x8cc): undefined reference to `glTranslatef'
graph3d.cpp:(.text+0x8f2): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x918): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x93e): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x9a6): undefined reference to `glCallList'
graph3d.cpp:(.text+0x9bf): undefined reference to `glCallList'
graph3d.cpp:(.text+0x9d3): undefined reference to `glCallList'
graph3d.cpp:(.text+0x9e7): undefined reference to `glCallList'
graph3d.cpp:(.text+0xa10): undefined reference to `glNewList'
graph3d.cpp:(.text+0xa33): undefined reference to `glLineWidth'
graph3d.cpp:(.text+0xa3f): undefined reference to `glBegin'
graph3d.cpp:(.text+0xa5b): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xa73): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xa8b): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xaa7): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xabf): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xad7): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xaf3): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xb0b): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xb23): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xb28): undefined reference to `glEnd'
graph3d.cpp:(.text+0xb2d): undefined reference to `glEndList'
graph3d.cpp:(.text+0xc07): undefined reference to `glNewList'
graph3d.cpp:(.text+0xc2a): undefined reference to `glLineWidth'
graph3d.cpp:(.text+0xc5a): undefined reference to `glBegin'
graph3d.cpp:(.text+0xc76): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xcda): undefined reference to `glVertex3d'
graph3d.cpp:(.text+0xcee): undefined reference to `glEnd'
graph3d.cpp:(.text+0xd4c): undefined reference to `glBegin'
graph3d.cpp:(.text+0xd68): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xdcc): undefined reference to `glVertex3d'
graph3d.cpp:(.text+0xde0): undefined reference to `glEnd'
graph3d.cpp:(.text+0xe13): undefined reference to `glEndList'
.obj/graph3d.o: In function `graph3d::resizeGL(int, int)':
graph3d.cpp:(.text+0x3ef): undefined reference to `glMatrixMode'
collect2: ld returned 1 exit status
make: *** [graphcalc] Error 1

```

---

### Post by stevek123 on 2008-09-22
I got it figured out, compiled and installed!!! It was a tough build with a quirky setup and it really doesnt work very well BUT I had turned it into a mission... Mission accomplished :) . 1st need gmp installed, then to compile CLN & install. Then compile and install ginac. You need qt3 and its -dev files. You do need the -dev files for kde libs and -lglut also. The '...gl' errors I posted before were not opengl headers but rather kde & glut headers. 

graphcalc itself doesnt have a config file. It uses qmake instead of ./configure to generate the makefile. I figured out that when you have all your ducks in a row (above), you run qmake and generate the makefile. Open the Makefile and change -I/usr/kde/3.1/  on the INCPATH line to your kde version (I changed 3.1 to 4.4 = mine). Do the same for LIBS. Then add -lglut -lGLU -lGL to the LIBS variable as well. DONT rerun qmake! this will overwrite your makefile changes. Run make directly after saving your edited makefile. Mine FINALLY compiled with that. When it compiles, run ./graphcalc to generate the executable prog. 

Honestly, graphcalc was not worth the effort except as a good practice in learning the compiling of binaries. extcalc and genius in the repositories are both greatly superior progs. I really get the impression this graphcalc was someone's first attempt at linux programming and was left unfinished and unsupported.

---

### Post by stevek123 on 2008-09-22
Hey nowshining. I posted a thanks to you - not necessarily for that post but for your continued attention during my 'project'. Your comments kept me on track and were greatly appreciated. 
Steve

---

### Post by nowshining on 2008-09-22
> **stevek123 said:**
> I got it figured out, compiled and installed!!! It was a tough build with a quirky setup and it really doesnt work very well BUT I had turned it into a mission... Mission accomplished :) . 1st need gmp installed, then to compile CLN & install. Then compile and install ginac. You need qt3 and its -dev files. You do need the -dev files for kde libs and -lglut also. The '...gl' errors I posted before were not opengl headers but rather kde & glut headers. 

graphcalc itself doesnt have a config file. It uses qmake instead of ./configure to generate the makefile. I figured out that when you have all your ducks in a row (above), you run qmake and generate the makefile. Open the Makefile and change -I/usr/kde/3.1/  on the INCPATH line to your kde version (I changed 3.1 to 4.4 = mine). Do the same for LIBS. Then add -lglut -lGLU -lGL to the LIBS variable as well. DONT rerun qmake! this will overwrite your makefile changes. Run make directly after saving your edited makefile. Mine FINALLY compiled with that. When it compiles, run ./graphcalc to generate the executable prog. 

Honestly, graphcalc was not worth the effort except as a good practice in learning the compiling of binaries. extcalc and genius in the repositories are both greatly superior progs. I really get the impression this graphcalc was someone's first attempt at linux programming and was left unfinished and unsupported.

well here's a pre-makefile for anyone else, one may need to change some things, etc.. but should give u graphical look on how it should look then just run make it will/should stop at codes it may seem and if it doesn't give an error, do ./graphcalc and hit enter and now it should show up fine.. :)

```
 
#############################################################################
# Makefile for building: graphcalc
# Generated by qmake (1.07a) (Qt 3.3.7) on: Sat Sep 20 22:35:37 2008
# Project:  graphcalc.pro
# Template: app
# Command: $(QMAKE) -o Makefile graphcalc.pro
#############################################################################

####### Compiler, tools and options

CC       = gcc
CXX      = g++
LEX      = flex
YACC     = yacc
CFLAGS   = -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT
CXXFLAGS = -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT
LEXFLAGS = 
YACCFLAGS= -d
INCPATH  = -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/kde -I/usr/include/qt3 -I.ui/ -I. -I.moc/
LINK     = g++
LFLAGS   = 
LIBS     = $(SUBLIBS) -L/usr/share/qt3/lib -L/usr/X11R6/lib -L/usr/lib -L/usr/kde/3.1/lib -lginac -lcln -lgmp -lqt-mt -lXext -lX11 -lm -lpthread -lglut -lGLU -lGL
AR       = ar cqs
RANLIB   = 
MOC      = /usr/share/qt3/bin/moc
UIC      = /usr/share/qt3/bin/uic
QMAKE    = qmake
TAR      = tar -cf
GZIP     = gzip -9f
COPY     = cp -f
COPY_FILE= $(COPY)
COPY_DIR = $(COPY) -r
INSTALL_FILE= $(COPY_FILE)
INSTALL_DIR = $(COPY_DIR)
DEL_FILE = rm -f
SYMLINK  = ln -sf
DEL_DIR  = rmdir
MOVE     = mv -f
CHK_DIR_EXISTS= test -d
MKDIR    = mkdir -p

####### Output directory

OBJECTS_DIR = .obj/

####### Files

HEADERS = expression.h \
		graph2d.h \
		graph3d.h
SOURCES = main.cpp \
		expression.cpp \
		graph2d.cpp \
		graph3d.cpp
OBJECTS = .obj/main.o \
		.obj/expression.o \
		.obj/graph2d.o \
		.obj/graph3d.o \
		.obj/mainform.o \
		.obj/about.o \
		.obj/graph2doptions.o \
		.obj/graph3doptions.o \
		.obj/graph3drendermodes.o \
		.obj/outputmode.o \
		.obj/qmake_image_collection.o
FORMS = mainform.ui \
		about.ui \
		graph2doptions.ui \
		graph3doptions.ui \
		graph3drendermodes.ui \
		outputmode.ui
UICDECLS = .ui/mainform.h \
		.ui/about.h \
		.ui/graph2doptions.h \
		.ui/graph3doptions.h \
		.ui/graph3drendermodes.h \
		.ui/outputmode.h
UICIMPLS = .ui/mainform.cpp \
		.ui/about.cpp \
		.ui/graph2doptions.cpp \
		.ui/graph3doptions.cpp \
		.ui/graph3drendermodes.cpp \
		.ui/outputmode.cpp
SRCMOC   = .moc/moc_graph3d.cpp \
		.moc/moc_mainform.cpp \
		.moc/moc_about.cpp \
		.moc/moc_graph2doptions.cpp \
		.moc/moc_graph3doptions.cpp \
		.moc/moc_graph3drendermodes.cpp \
		.moc/moc_outputmode.cpp
OBJMOC = .obj/moc_graph3d.o \
		.obj/moc_mainform.o \
		.obj/moc_about.o \
		.obj/moc_graph2doptions.o \
		.obj/moc_graph3doptions.o \
		.obj/moc_graph3drendermodes.o \
		.obj/moc_outputmode.o
DIST	   = graphcalc.pro
QMAKE_TARGET = graphcalc
DESTDIR  = 
TARGET   = graphcalc

first: all
####### Implicit rules

.SUFFIXES: .c .o .cpp .cc .cxx .C

.cpp.o:
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

.cc.o:
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

.cxx.o:
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

.C.o:
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o $@ $<

.c.o:
	$(CC) -c $(CFLAGS) $(INCPATH) -o $@ $<

####### Build rules

all: Makefile $(TARGET)

$(TARGET):  $(UICDECLS) $(OBJECTS) $(OBJMOC)  
	$(LINK) $(LFLAGS) -o $(TARGET) $(OBJECTS) $(OBJMOC) $(OBJCOMP) $(LIBS)

mocables: $(SRCMOC)
uicables: $(UICDECLS) $(UICIMPLS)

$(MOC): 
	( cd $(QTDIR)/src/moc && $(MAKE) )

Makefile: graphcalc.pro  /usr/share/qt3/mkspecs/default/qmake.conf /usr/share/qt3/lib/libqt-mt.prl
	$(QMAKE) -o Makefile graphcalc.pro
qmake: 
	@$(QMAKE) -o Makefile graphcalc.pro

dist: 
	@mkdir -p .obj/graphcalc && $(COPY_FILE) --parents $(SOURCES) $(HEADERS) $(FORMS) $(DIST) .obj/graphcalc/ && $(COPY_FILE) --parents images/zoomin.png images/zoomout.png images/zoomprevious.png images/zoomstandard.png images/idr_main.png .obj/graphcalc/ && $(COPY_FILE) --parents mainform.ui.h graph2doptions.ui.h graph3doptions.ui.h .obj/graphcalc/ && ( cd `dirname .obj/graphcalc` && $(TAR) graphcalc.tar graphcalc && $(GZIP) graphcalc.tar ) && $(MOVE) `dirname .obj/graphcalc`/graphcalc.tar.gz . && $(DEL_FILE) -r .obj/graphcalc

mocclean:
	-$(DEL_FILE) $(OBJMOC)
	-$(DEL_FILE) $(SRCMOC)

uiclean:
	-$(DEL_FILE) $(UICIMPLS) $(UICDECLS)

yaccclean:
lexclean:
clean: mocclean uiclean
	-$(DEL_FILE) $(OBJECTS)
		-$(DEL_FILE) .ui/qmake_image_collection.cpp
	-$(DEL_FILE) *~ core *.core


####### Sub-libraries

distclean: clean
	-$(DEL_FILE) $(TARGET) $(TARGET)


FORCE:

####### Compile

.obj/main.o: main.cpp .ui/mainform.h \
		.ui/about.h \
		expression.h \
		.ui/graph2doptions.h \
		.ui/graph3doptions.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/main.o main.cpp

.obj/expression.o: expression.cpp expression.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/expression.o expression.cpp

.obj/graph2d.o: graph2d.cpp graph2d.h \
		expression.h \
		.ui/graph2doptions.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/graph2d.o graph2d.cpp

.obj/graph3d.o: graph3d.cpp expression.h \
		graph3d.h \
		.ui/graph3doptions.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/graph3d.o graph3d.cpp

.ui/mainform.h: mainform.ui graph2d.h \
		graph3d.h \
		.ui/about.h \
		expression.h \
		.ui/graph2doptions.h \
		.ui/graph3doptions.h
	$(UIC) mainform.ui -o .ui/mainform.h

.ui/mainform.cpp: .ui/mainform.h mainform.ui mainform.ui.h graph2d.h \
		graph3d.h \
		.ui/about.h \
		expression.h \
		.ui/graph2doptions.h \
		.ui/graph3doptions.h
	$(UIC) mainform.ui -i mainform.h -o .ui/mainform.cpp

.ui/about.h: about.ui 
	$(UIC) about.ui -o .ui/about.h

.ui/about.cpp: .ui/about.h about.ui 
	$(UIC) about.ui -i about.h -o .ui/about.cpp

.ui/graph2doptions.h: graph2doptions.ui 
	$(UIC) graph2doptions.ui -o .ui/graph2doptions.h

.ui/graph2doptions.cpp: .ui/graph2doptions.h graph2doptions.ui graph2doptions.ui.h 
	$(UIC) graph2doptions.ui -i graph2doptions.h -o .ui/graph2doptions.cpp

.ui/graph3doptions.h: graph3doptions.ui 
	$(UIC) graph3doptions.ui -o .ui/graph3doptions.h

.ui/graph3doptions.cpp: .ui/graph3doptions.h graph3doptions.ui graph3doptions.ui.h 
	$(UIC) graph3doptions.ui -i graph3doptions.h -o .ui/graph3doptions.cpp

.ui/graph3drendermodes.h: graph3drendermodes.ui 
	$(UIC) graph3drendermodes.ui -o .ui/graph3drendermodes.h

.ui/graph3drendermodes.cpp: .ui/graph3drendermodes.h graph3drendermodes.ui 
	$(UIC) graph3drendermodes.ui -i graph3drendermodes.h -o .ui/graph3drendermodes.cpp

.ui/outputmode.h: outputmode.ui 
	$(UIC) outputmode.ui -o .ui/outputmode.h

.ui/outputmode.cpp: .ui/outputmode.h outputmode.ui 
	$(UIC) outputmode.ui -i outputmode.h -o .ui/outputmode.cpp

.obj/mainform.o: .ui/mainform.cpp mainform.ui.h \
		.ui/mainform.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/mainform.o .ui/mainform.cpp

.obj/about.o: .ui/about.cpp .ui/about.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/about.o .ui/about.cpp

.obj/graph2doptions.o: .ui/graph2doptions.cpp graph2doptions.ui.h \
		.ui/graph2doptions.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/graph2doptions.o .ui/graph2doptions.cpp

.obj/graph3doptions.o: .ui/graph3doptions.cpp graph3doptions.ui.h \
		.ui/graph3doptions.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/graph3doptions.o .ui/graph3doptions.cpp

.obj/graph3drendermodes.o: .ui/graph3drendermodes.cpp .ui/graph3drendermodes.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/graph3drendermodes.o .ui/graph3drendermodes.cpp

.obj/outputmode.o: .ui/outputmode.cpp .ui/outputmode.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/outputmode.o .ui/outputmode.cpp

.obj/moc_graph3d.o: .moc/moc_graph3d.cpp  graph3d.h .ui/graph3doptions.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/moc_graph3d.o .moc/moc_graph3d.cpp

.obj/moc_mainform.o: .moc/moc_mainform.cpp  .ui/mainform.h .ui/about.h \
		expression.h \
		.ui/graph2doptions.h \
		.ui/graph3doptions.h
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/moc_mainform.o .moc/moc_mainform.cpp

.obj/moc_about.o: .moc/moc_about.cpp  .ui/about.h 
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/moc_about.o .moc/moc_about.cpp

.obj/moc_graph2doptions.o: .moc/moc_graph2doptions.cpp  .ui/graph2doptions.h 
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/moc_graph2doptions.o .moc/moc_graph2doptions.cpp

.obj/moc_graph3doptions.o: .moc/moc_graph3doptions.cpp  .ui/graph3doptions.h 
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/moc_graph3doptions.o .moc/moc_graph3doptions.cpp

.obj/moc_graph3drendermodes.o: .moc/moc_graph3drendermodes.cpp  .ui/graph3drendermodes.h 
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/moc_graph3drendermodes.o .moc/moc_graph3drendermodes.cpp

.obj/moc_outputmode.o: .moc/moc_outputmode.cpp  .ui/outputmode.h 
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/moc_outputmode.o .moc/moc_outputmode.cpp

.moc/moc_graph3d.cpp: $(MOC) graph3d.h
	$(MOC) graph3d.h -o .moc/moc_graph3d.cpp

.moc/moc_mainform.cpp: $(MOC) .ui/mainform.h
	$(MOC) .ui/mainform.h -o .moc/moc_mainform.cpp

.moc/moc_about.cpp: $(MOC) .ui/about.h
	$(MOC) .ui/about.h -o .moc/moc_about.cpp

.moc/moc_graph2doptions.cpp: $(MOC) .ui/graph2doptions.h
	$(MOC) .ui/graph2doptions.h -o .moc/moc_graph2doptions.cpp

.moc/moc_graph3doptions.cpp: $(MOC) .ui/graph3doptions.h
	$(MOC) .ui/graph3doptions.h -o .moc/moc_graph3doptions.cpp

.moc/moc_graph3drendermodes.cpp: $(MOC) .ui/graph3drendermodes.h
	$(MOC) .ui/graph3drendermodes.h -o .moc/moc_graph3drendermodes.cpp

.moc/moc_outputmode.cpp: $(MOC) .ui/outputmode.h
	$(MOC) .ui/outputmode.h -o .moc/moc_outputmode.cpp

.obj/qmake_image_collection.o: .ui/qmake_image_collection.cpp
	$(CXX) -c $(CXXFLAGS) $(INCPATH) -o .obj/qmake_image_collection.o .ui/qmake_image_collection.cpp

.ui/qmake_image_collection.cpp: images/zoomin.png \
		images/zoomout.png \
		images/zoomprevious.png \
		images/zoomstandard.png \
		images/idr_main.png
	$(UIC)  -embed graphcalc images/zoomin.png images/zoomout.png images/zoomprevious.png images/zoomstandard.png images/idr_main.png -o .ui/qmake_image_collection.cpp

####### Install

install:  

uninstall:  



```

---

### Post by nowshining on 2008-09-22
> **stevek123 said:**
> Hey nowshining. I posted a thanks to you - not necessarily for that post but for your continued attention during my 'project'. Your comments kept me on track and were greatly appreciated. 
Steve

thanks - :) i'm happy u got it figured out and u also helped me in the process so in the end both of us helped each other.. :)

---

### Post by CPImmanuel on 2008-11-22
I have somewhat of a similar problem. Can anyone help? I have been trying to compile the make the program PGCalc, which is a KDE app. The configure step stops with the error:
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!

Is there some other set of files that I need to install?
I went past the Qt error and the KDE header error by installing files that I found under Synaptic which made sense...but now I am stuck again!

Thanks.
Paul

---

